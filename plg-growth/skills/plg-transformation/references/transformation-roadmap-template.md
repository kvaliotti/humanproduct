# PLG Transformation Roadmap Template

A phased plan for organizational PLG transformation. Customize based on the Four Dimensions assessment scores. Each phase builds on the previous one -- do not skip phases.

---

## Phase 0: Foundation (Quarter 1)

**Objective:** Establish the conditions for PLG transformation. Without this phase, subsequent phases will fail due to lack of sponsorship, budget, or alignment.

### Key Results
| Key Result | Measure | Target |
|-----------|---------|--------|
| Executive sponsor secured | VP+ level person owns PLG outcomes | Named sponsor with quarterly review commitment |
| Four Dimensions assessment completed | Scorecard across all 4 dimensions | Scores documented, gaps identified |
| Business case approved | ROI model for PLG investment | Budget allocated for Phase 1 |
| Growth PM hired or assigned | Dedicated person owns growth | PM in role, not a side responsibility |
| Basic tracking live | Core events firing (signup, activation, payment) | TASE Track score >= 2 |

### Activities
1. **Executive education:** Present the PLG case to leadership. Use competitor analysis, market trends, and TAM analysis to show why PLG matters.
2. **Four Dimensions assessment:** Run the assessment (use the four-dimensions reference). Score each dimension. Identify gaps.
3. **Business case:** Model the ROI of PLG investment. Compare self-serve CAC vs sales CAC. Model the impact of improving activation rate, conversion rate, or expansion.
4. **Hire/assign Growth PM:** If no dedicated growth PM exists, this is the #1 hire. This person will drive Phases 1-3.
5. **Initial tracking:** Implement the minimum tracking plan: user_signed_up, activation_achieved (define what activation means), subscription_created. This enables Phase 1 analysis.

### Team Requirements
- Growth PM (1 FTE -- can be existing PM reassigned)
- Engineering support (0.5 FTE for tracking implementation)
- Executive sponsor (10% time for reviews and decisions)

### Risk Factors
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| No executive buy-in | High (if PLG is new to the org) | Critical -- blocks everything | Start with a small pilot instead of full transformation |
| Cannot define activation metric | Medium | High -- blocks measurement | Use retention correlation analysis; start with best guess, refine later |
| Tracking implementation delayed | Medium | Medium -- delays Phase 1 | Use simplest possible implementation; CDP can come later |

### Exit Criteria
- [ ] Executive sponsor named and committed
- [ ] Four Dimensions scores documented
- [ ] Business case approved with budget
- [ ] Growth PM in role
- [ ] Core tracking events firing and validated

---

## Phase 1: Instrument (Quarter 2)

**Objective:** Build the data foundation for PLG execution. You cannot optimize what you cannot measure.

### Key Results
| Key Result | Measure | Target |
|-----------|---------|--------|
| Full tracking plan implemented | Events across all AARMS stages | >= 15 events live and validated |
| AARMS dashboards built | Dashboard per stage | All 5 stages have basic dashboards |
| Activation metric defined and measured | Correlation analysis complete | Activation action identified, baseline rate established |
| First experiments run | Completed experiments | >= 3 experiments with results documented |
| Experiment process established | Written process, template, review cadence | Template in use, weekly experiment review |

### Activities
1. **Tracking plan:** Use the tracking-plan-template reference. Implement events for all AARMS stages. Validate data quality.
2. **AARMS dashboards:** Build one dashboard per stage using the TASE Analyse framework. Start with acquisition funnel, activation funnel, retention curves.
3. **Activation metric:** Correlate early user behaviors (first 7-14 days) with D30 retention. Identify the action most predictive of retention. Set this as the activation metric.
4. **First experiments:** Run 3 simple experiments to build the muscle. Start with high-confidence, low-effort tests (signup form optimization, onboarding copy, email timing).
5. **Experiment process:** Create the experiment brief template. Run experiment review meetings. Document results.

### Team Requirements
- Growth PM (1 FTE)
- Engineers (2 FTE -- tracking implementation + experiment builds)
- Analyst (0.5-1 FTE -- dashboard building, activation analysis)
- Designer (0.5 FTE -- experiment design support)

### Risk Factors
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Data quality issues | High | High -- wrong data = wrong decisions | Implement QA checks; validate against billing system |
| Dashboard not used | Medium | Medium -- dashboards without viewers are waste | Start with weekly dashboard review meeting; make leadership attend |
| Experiments fail to reach significance | Medium | Low -- learning, not failure | Set realistic MDE; start with high-traffic areas |

### Exit Criteria
- [ ] >= 15 tracking events live with < 5% data quality issues
- [ ] All 5 AARMS dashboards built and reviewed weekly
- [ ] Activation metric defined with baseline rate
- [ ] >= 3 experiments completed with documented results
- [ ] Experiment process in use (template, review, documentation)

---

## Phase 2: Activate (Quarters 3-4)

**Objective:** Optimize the activation funnel, build the first growth loop, and establish PLG-native goals.

### Key Results
| Key Result | Measure | Target |
|-----------|---------|--------|
| Activation rate improved | Activation metric | +[X]% from baseline (set based on sensitivity analysis) |
| First growth loop built | Viral, content, or data loop operational | Loop identified, instrumented, and optimized |
| PQA/PQL scoring launched | Product-qualified accounts/leads scored | Scoring model live, sales team using scores |
| PLG-native goals set | Goals from revenue driver tree | All growth team goals are PLG-native metrics |
| Dedicated growth team formed | Cross-functional team with dedicated resources | PM + designer + 2-4 engineers + analyst |

### Activities
1. **Activation optimization:** Use the activation issue tree. Diagnose bottlenecks (B=MAT analysis). Run experiments targeting the activation funnel. Target: measurable improvement in activation rate.
2. **Growth loop:** Identify the most viable growth loop for this product (viral invite, content creation, data network effect, etc.). Instrument the loop. Measure loop velocity. Optimize the weakest link.
3. **PQA/PQL scoring:** Define scoring model based on product usage signals. Sync scores to CRM. Train sales team on PQL workflow. Measure PQL conversion rate.
4. **PLG-native goals:** Replace traditional goals with revenue-tree-derived metrics. Every team goal connects to a specific tree branch. Include leading indicators.
5. **Growth team formation:** If not already done, form a dedicated cross-functional growth team with PM + designer + engineers + analyst. Use OST as the operating system.

### Team Requirements
- Growth PM (1 FTE)
- Engineers (3-4 FTE -- experiment velocity requires dedicated capacity)
- Analyst (1 FTE -- experiment analysis, scoring model, cohort analysis)
- Designer (1 FTE -- activation UX, experiment design)
- Data/ML engineer (0.5 FTE -- PQL scoring model)

### Risk Factors
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Activation rate plateaus | Medium | Medium -- diminishing returns | Reassess activation definition; expand to multi-action activation |
| Sales resistance to PQL | High | High -- PQL ignored = no sales-assist benefit | Co-design scoring with sales; start with high-confidence PQLs only |
| Goal-setting resistance | Medium | Medium -- teams prefer familiar goals | Show the math: how tree-derived goals connect to revenue |

### Exit Criteria
- [ ] Activation rate improved by [X]% from Phase 1 baseline
- [ ] Growth loop instrumented and showing positive velocity
- [ ] PQL scoring live and used by sales team
- [ ] All growth team goals are PLG-native
- [ ] Dedicated growth team operational with weekly cadence

---

## Phase 3: Scale (Quarters 5-8)

**Objective:** Expand PLG across all AARMS stages, build product-led sales motion, and scale experimentation.

### Key Results
| Key Result | Measure | Target |
|-----------|---------|--------|
| All AARMS stages optimized | Experiments run per stage | >= 3 experiments per stage per quarter |
| Product-led sales motion operational | PQL pipeline contribution | PQL pipeline >= [X]% of total pipeline |
| Monetisation optimized | Free-to-paid conversion, ARPA, expansion | Each metric improved from Phase 2 baseline |
| Experimentation scaled | Experiment velocity | >= 10 experiments per quarter |
| OST as team operating system | Teams using OST | All growth teams have active OSTs |

### Activities
1. **Expand to all AARMS stages:** Systematically address each stage. Prioritize by revenue tree sensitivity.
2. **Product-led sales:** Build the full PLS motion: PQL scoring -> sales alerts -> sales playbook for PQLs -> measure PQL vs traditional pipeline conversion.
3. **Monetisation optimization:** Pricing, packaging, paywall design, upgrade flows, expansion prompts, dunning. Run experiments on each.
4. **Scale experimentation:** Increase experiment velocity. Invest in infrastructure (faster feature flags, automated analysis, self-serve experiment design).
5. **OST rollout:** Roll OST to all growth teams. Train PMs, run monthly OST reviews, share learnings cross-team.

### Team Requirements
- Growth PMs (3-5 FTE, depending on scope)
- Engineers (8-12 FTE across teams)
- Analysts (2-3 FTE)
- Designers (2-3 FTE)
- Growth lead/director (1 FTE -- leads the growth org)

### Risk Factors
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Team grows too fast | Medium | Medium -- culture diluted | Hire deliberately; onboard into PLG culture; maintain rituals |
| Experiment interference | Medium | High -- overlapping experiments contaminate results | Experiment registry, mutual exclusion rules, analyst oversight |
| Product-led sales friction | High | High -- sales ignores or misuses PQLs | Joint design with sales leadership; measure and share PQL conversion data |

---

## Phase 4: Transform (Ongoing)

**Objective:** PLG becomes the organizational operating model, not a special initiative.

### Key Results
| Key Result | Measure | Target |
|-----------|---------|--------|
| Org restructured around revenue tree | Team structure matches revenue components | Each revenue component has a dedicated team |
| Culture is experimentation-first | Experiment velocity, failure sharing | >= 20 experiments/quarter, monthly learning shares |
| PLG metrics replace sales-led metrics | Board deck metrics | Primary metrics are activation, NDR, self-serve revenue |
| Leadership adopts PLG cadence | Quarterly revenue tree reviews | Leadership uses tree for resource allocation |
| New hires onboarded into PLG | Onboarding includes PLG philosophy | All new PMs, engineers, designers trained on PLG |

### Activities
1. **Org restructure:** Move from functional silos to revenue-tree-aligned teams. Each team owns a revenue component or AARMS stage. Use the team-structuring reference.
2. **Culture embedding:** PLG thinking becomes default. Experimentation is expected, not exceptional. Failure is shared publicly. Data overrules opinion.
3. **Metric transformation:** Board deck leads with PLG metrics (activation rate, NDR, self-serve revenue, experiment velocity). Traditional sales metrics become secondary.
4. **Leadership cadence:** Quarterly revenue tree reviews drive resource allocation. Goals are set from tree sensitivity analysis. Leadership models data-driven behavior.
5. **Continuous improvement:** The transformation is never "done." Continuously refine processes, team structures, and tools based on what the data says.

### This Phase Never Ends
Phase 4 is not a destination. It is the ongoing state of being product-led. The organization continuously:
- Refines its understanding of the revenue driver tree
- Shifts resources to the highest-sensitivity areas
- Runs more and better experiments
- Learns faster than competitors

---

## Phase Dependencies

```
Phase 0: Foundation
    |
    └── Requires: Executive sponsor, budget, Growth PM
    
Phase 1: Instrument
    |
    ├── Requires: Phase 0 complete
    └── Requires: Engineering capacity for tracking
    
Phase 2: Activate
    |
    ├── Requires: Phase 1 complete (data + dashboards + first experiments)
    └── Requires: Dedicated growth team
    
Phase 3: Scale
    |
    ├── Requires: Phase 2 complete (activation optimized, PLG-native goals)
    └── Requires: Expanded team, experimentation infrastructure
    
Phase 4: Transform
    |
    ├── Requires: Phase 3 demonstrating results
    └── Requires: Organizational willingness to restructure
```

---

## Customization Based on Assessment Scores

### If Strategic Alignment is Low (1-2)
- **Extend Phase 0** to 2 quarters. The business case and executive education take longer.
- **Add:** Competitor PLG analysis, market trend presentation, small pilot to demonstrate value.
- **Risk:** Without alignment, the transformation stalls after Phase 1. Get the sponsor first.

### If Goal Setting is Low (1-2)
- **Phase 1 must include** revenue driver tree construction and sensitivity analysis before experimentation.
- **Add:** Workshop with leadership to co-create the tree. Show how tree-derived goals are more actionable.
- **Risk:** Teams optimize for wrong metrics. Wrong goals = wasted experiments.

### If Org Structure is Low (1-2)
- **Phase 2 must include** growth team formation as a prerequisite for activation work.
- **Add:** Role definitions, hiring plan, reporting structure decision.
- **Risk:** Growth work gets done by PMs with 20% capacity. Nothing ships fast enough. Demoralization.

### If Org Culture is Low (1-2)
- **Thread culture change through EVERY phase**, not as Phase 4.
- Phase 0: Leadership models data-driven behavior
- Phase 1: Run experiments and share results publicly
- Phase 2: Celebrate experiment failures as learnings
- Phase 3: Make experimentation a hiring criterion
- **Risk:** Process without culture = compliance theater. People follow the template but not the spirit.
