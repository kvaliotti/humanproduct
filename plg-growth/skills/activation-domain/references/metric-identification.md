# Activation Metric Identification

Comprehensive methodology for finding the product event (or combination of events) that best predicts long-term user success. Use multiple methods and triangulate.

---

## Method 1: CSI / Aha Score (Primary)

The Composite Success Index adapts precision/recall concepts to find which early user action best separates retained users from churned users.

### Step-by-Step Process

**1. Build the event list**
List every meaningful product event (actions users take):
- Example: created_project, invited_teammate, uploaded_file, ran_report, connected_integration, sent_message, created_template, etc.
- Exclude trivial events: page_view, button_hover, tooltip_shown
- Include 15-50 events typically

**2. Define volume thresholds**
For each event, test multiple volume levels:
- Did the event at least 1 time
- Did the event at least 2 times
- Did the event at least 3 times
- Did the event at least 5 times
- Did the event at least 10 times

**3. Define the time window**
Test multiple windows:
- Within first 7 days of signup
- Within first 14 days of signup
- Within first 30 days of signup

14 days is the most common sweet spot for PLG SaaS.

**4. Define the retention outcome**
Choose a retention definition:
- Active in month 2 (30-60 days post-signup) -- most common
- Active in month 3 (60-90 days) -- more conservative
- Still paying at 90 days -- if monetization is the goal

**5. Build the 2x2 contingency table**

For each (event, volume threshold, time window) combination:

```
                    Retained    Not Retained
Did Event ≥ N         TP           FP
Did NOT Event ≥ N     FN           TN
```

Where:
- TP (True Positive): Did the event AND retained
- FP (False Positive): Did the event AND did NOT retain
- FN (False Negative): Did NOT do the event AND retained
- TN (True Negative): Did NOT do the event AND did NOT retain

**6. Calculate CSI Score**

```
CSI = TP / (TP + FP + FN)
```

This is equivalent to the Jaccard Index / Intersection over Union (IoU).

**Score interpretation:**
- CSI > 0.5: Strong predictor. This event strongly separates retained from churned.
- CSI 0.3 - 0.5: Moderate predictor. Useful as supporting behavior.
- CSI < 0.3: Weak predictor. Not suitable as activation metric.

**7. Rank all combinations**

Sort by CSI score descending. The top result is your activation metric candidate.

### Pseudocode

```python
import pandas as pd

# users_df: user_id, signup_date, is_retained (bool)
# events_df: user_id, event_name, event_date

def calculate_csi(users_df, events_df, event_name, threshold, days_window):
    # Filter events within the time window
    events_in_window = events_df[
        (events_df['event_name'] == event_name) &
        (events_df['event_date'] - events_df['signup_date']).dt.days <= days_window
    ]
    
    # Count events per user
    event_counts = events_in_window.groupby('user_id').size().reset_index(name='count')
    
    # Flag users who met threshold
    users_met = set(event_counts[event_counts['count'] >= threshold]['user_id'])
    
    # Build 2x2 table
    tp = len([u for u in users_df['user_id'] if u in users_met and users_df.loc[users_df['user_id']==u, 'is_retained'].values[0]])
    fp = len([u for u in users_df['user_id'] if u in users_met and not users_df.loc[users_df['user_id']==u, 'is_retained'].values[0]])
    fn = len([u for u in users_df['user_id'] if u not in users_met and users_df.loc[users_df['user_id']==u, 'is_retained'].values[0]])
    
    csi = tp / (tp + fp + fn) if (tp + fp + fn) > 0 else 0
    return csi

# Run for all combinations
results = []
for event in event_list:
    for threshold in [1, 2, 3, 5, 10]:
        for window in [7, 14, 30]:
            score = calculate_csi(users_df, events_df, event, threshold, window)
            results.append({
                'event': event,
                'threshold': threshold,
                'window_days': window,
                'csi_score': score
            })

results_df = pd.DataFrame(results).sort_values('csi_score', ascending=False)
```

### Practical Tips
- Need at least 500 users with 60+ days of history for reliable results
- If top CSI scores are clustered (within 0.05 of each other), use qualitative data to choose
- The threshold matters: "created 3 projects in 14 days" is more specific than "created 1 project ever"
- Test if the metric is consistent across cohorts (not just one anomalous month)

---

## Method 2: Information Value / Weight of Evidence

Adapted from credit scoring. Measures how well a variable (event) separates two groups (retained vs. churned).

### Process

**1. Bin the event counts**
For a given event, create bins based on how many times users did it:
- Bin 1: 0 times
- Bin 2: 1 time
- Bin 3: 2-3 times
- Bin 4: 4-5 times
- Bin 5: 6+ times

**2. Calculate Weight of Evidence per bin**

```
WoE_i = ln(Distribution_Retained_i / Distribution_Churned_i)
```

Where Distribution = (count in bin for group) / (total in group)

**3. Calculate Information Value**

```
IV = Σ (Distribution_Retained_i - Distribution_Churned_i) × WoE_i
```

**IV interpretation:**
- IV > 0.5: Very strong predictor (may be overfitting -- verify)
- IV 0.3 - 0.5: Strong predictor
- IV 0.1 - 0.3: Medium predictor
- IV 0.02 - 0.1: Weak predictor
- IV < 0.02: Not predictive

### Pseudocode

```python
import numpy as np

def calculate_iv(users_df, events_df, event_name, bins=[0, 1, 2, 3, 5, 10, float('inf')]):
    # Count events per user
    event_counts = events_df[events_df['event_name'] == event_name].groupby('user_id').size()
    users_df['event_count'] = users_df['user_id'].map(event_counts).fillna(0)
    users_df['bin'] = pd.cut(users_df['event_count'], bins=bins, right=False)
    
    iv = 0
    for bin_label in users_df['bin'].unique():
        bin_data = users_df[users_df['bin'] == bin_label]
        dist_retained = len(bin_data[bin_data['is_retained']]) / len(users_df[users_df['is_retained']])
        dist_churned = len(bin_data[~bin_data['is_retained']]) / len(users_df[~users_df['is_retained']])
        
        if dist_retained > 0 and dist_churned > 0:
            woe = np.log(dist_retained / dist_churned)
            iv += (dist_retained - dist_churned) * woe
    
    return iv
```

---

## Method 3: Random Forest Feature Importance

Use machine learning to find which early actions best predict retention.

### Process

1. Create a feature matrix: one row per user, one column per event (count within time window)
2. Target variable: retained (1) or not (0)
3. Train a Random Forest classifier
4. Extract feature importances
5. Top features = activation metric candidates

### Pseudocode

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import cross_val_score

# Build feature matrix
features = events_df.pivot_table(
    index='user_id', columns='event_name', 
    values='event_date', aggfunc='count'
).fillna(0)

X = features.values
y = users_df.set_index('user_id').loc[features.index, 'is_retained'].values

# Train model
rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X, y)

# Extract importance
importance = pd.DataFrame({
    'event': features.columns,
    'importance': rf.feature_importances_
}).sort_values('importance', ascending=False)

# Cross-validate
cv_score = cross_val_score(rf, X, y, cv=5, scoring='roc_auc').mean()
print(f"Model AUC: {cv_score:.3f}")
```

### Caveats
- Requires 1000+ users for reliable results
- Correlated features can split importance (two similar events each get half)
- Model AUC should be > 0.65 for the features to be meaningfully predictive
- Feature importance tells you WHAT predicts, not WHY

---

## Method 4: Correlation Analysis

Simplest method. Quick sanity check, not sufficient alone.

### Process

For each event, calculate:
- Point-biserial correlation between (did event at least N times in window) and (retained)
- Compare correlation strength across events

```python
from scipy.stats import pointbiserialr

for event in event_list:
    did_event = users_df['user_id'].isin(
        events_df[events_df['event_name'] == event]['user_id']
    ).astype(int)
    corr, pvalue = pointbiserialr(did_event, users_df['is_retained'])
    print(f"{event}: r={corr:.3f}, p={pvalue:.4f}")
```

### Limitations
- Only captures linear relationships
- Does not account for volume thresholds
- Sensitive to base rates (if 90% of users do the event, correlation is misleading)

---

## Triangulation: Combining Methods

No single method is definitive. Use this decision framework:

1. **Run CSI as primary.** It is the most interpretable and directly actionable.
2. **Cross-check with IV.** If IV and CSI agree on the top event, high confidence.
3. **Use Random Forest for discovery.** It may surface events you did not think to test.
4. **Validate with qualitative interviews.** Does the quant metric match what users report as their aha moment?

### Decision Matrix

| CSI agrees with IV | Qual confirms | Decision |
|--------------------|---------------|----------|
| Yes | Yes | High confidence. Ship this as activation metric. |
| Yes | No | Investigate: quant may be capturing a proxy. Interview deeper. |
| No | - | Methods disagree. Use RF as tiebreaker. Interview for context. |
| - | Only qual data | Use qual insights to form hypothesis. Collect data to validate with CSI. |

### Minimum Viable Activation Metric

If data is limited (< 500 users), skip quant methods and use qualitative interviews only:
1. Interview 15-20 retained users
2. Ask: "When did you first feel the product was valuable?"
3. Cluster responses into product events
4. The most common event is your activation metric hypothesis
5. Validate with data as user base grows
