**Volume 46. Causality and Scientific AI**


# Chapter 03. Counterfactual Reasoning

##  

## 03.00. Overview

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Counterfactual reasoning extends causal analysis beyond observing what happened and estimating what would happen under an intervention. It asks what would have happened to the same individual, system, or situation if some relevant condition had been different. This ability transforms causal knowledge into a mechanism for comparing reality with alternative possibilities that were never simultaneously observed.

A counterfactual begins with a factual world containing observed variables, events, actions, and outcomes. Reasoning then constructs an alternative world in which one or more conditions are modified while appropriate background factors remain consistent. The resulting outcome is compared with the factual outcome, allowing a system to reason about alternative causes, decisions, failures, opportunities, and consequences.

This form of reasoning differs fundamentally from ordinary prediction. A predictive model may estimate the probability of an outcome from correlations in historical data, whereas counterfactual reasoning asks how the outcome would change if a specific causal factor were altered. Consequently, useful counterfactual inference requires knowledge about causal structure rather than merely an accurate statistical mapping between inputs and outputs.

Structural causal models provide a rigorous foundation for counterfactual reasoning. Variables are connected through structural equations representing causal mechanisms, while exogenous variables encode background conditions that are not explained within the model. Once the observed situation is associated with plausible values of these background variables, the model can modify a causal mechanism and simulate an alternative outcome.

A common conceptual procedure consists of abduction, action, and prediction. During abduction, observed evidence is used to infer the latent background circumstances that could have generated the factual situation. During action, a selected causal relationship is modified according to the hypothetical condition. During prediction, the modified causal system is evaluated to determine the corresponding counterfactual outcome.

Counterfactual reasoning therefore operates at a deeper level than association and intervention alone. Association asks what tends to occur when variables are observed together, while intervention asks what is expected to occur when a variable is deliberately changed. Counterfactual reasoning additionally conditions the hypothetical analysis on what is already known about a particular realized case, connecting causal mechanisms with individual situations.

The distinction is especially important because factual and counterfactual outcomes for the same case generally cannot both be observed. If a robot selected path A, the exact same episode cannot simultaneously reveal what would have occurred had it selected path B. Counterfactual inference must therefore reconstruct the missing alternative through causal assumptions, structural knowledge, uncertainty modeling, experimental evidence, or combinations of these sources.

Counterfactual questions can concern actions, environmental conditions, internal states, or causal mechanisms. An engineer may ask whether a failure would have occurred without a temperature increase, a physician may consider an outcome without a treatment, and an autonomous agent may evaluate whether another action would have avoided a collision. Despite different domains, each question compares an observed trajectory against a causally modified alternative.

This capability is closely related to explanation. Saying that two variables are correlated does not establish that changing one would have prevented an outcome. A stronger explanation evaluates whether the outcome would remain unchanged when the suspected cause is removed or modified. Counterfactual dependence can therefore help identify which factors were causally important to a particular event and distinguish them from coincidental associations.

Counterfactuals are also central to decision making because intelligent agents must evaluate actions that they did not actually execute. After observing an outcome, an agent can ask whether another decision would have produced a better result. Repeated counterfactual evaluation supports policy improvement, regret analysis, planning, credit assignment, and learning from limited experience without physically executing every conceivable alternative action.

For AI explainability, counterfactual reasoning provides an intuitive form of explanation based on meaningful changes. Instead of only reporting feature importance, a system can describe which changes would have altered its decision. For example, a counterfactual explanation may indicate that an output would have changed if a small set of causally relevant conditions had differed, making model behavior easier to examine and challenge.

In robotics, counterfactual reasoning can become part of a perception--prediction--action loop. A robot observes the current world, estimates causal state, considers candidate interventions, predicts alternative future trajectories, and chooses an action according to expected consequences. After execution, discrepancies between predicted and observed outcomes can refine the causal model, gradually improving planning and adaptation in unfamiliar environments.

Counterfactual simulation becomes particularly valuable when real experimentation is expensive, dangerous, slow, or irreversible. Industrial systems can examine alternative operating parameters before modifying equipment, autonomous vehicles can evaluate avoided-collision scenarios, and scientific AI systems can explore hypothetical mechanisms before conducting experiments. Such reasoning can reduce unnecessary interventions while directing physical experiments toward informative alternatives.

However, counterfactual conclusions are only as reliable as the causal assumptions supporting them. Incorrect graph structures, missing confounders, inaccurate structural equations, distribution shifts, or poorly modeled latent variables can produce convincing but invalid alternative worlds. Counterfactual systems therefore require uncertainty estimation, sensitivity analysis, causal validation, and explicit documentation of assumptions rather than treating simulated alternatives as observed facts.

Another challenge is defining which aspects of the factual world should remain unchanged. Unrealistic counterfactuals may modify one variable while ignoring other variables that must causally change with it. Effective reasoning must respect feasibility, temporal consistency, physical constraints, and causal dependencies so that alternative scenarios represent coherent worlds rather than arbitrary combinations of values that could never occur.

Counterfactual reasoning also connects naturally with world models and model-based intelligence. A sufficiently structured world model should represent not only likely future states but also how those states respond to alternative actions and causal changes. This allows an intelligent system to move from forecasting a single probable future toward evaluating multiple possible futures generated by different decisions, interventions, and environmental conditions.

Within the broader structure of causality and scientific AI, counterfactual reasoning therefore serves as a bridge between structural causal knowledge and intelligent action. The chapter progresses from what-if reasoning and counterfactual models to interventions, estimation, causal explanation, and applications in decision systems, explainable AI, and robotics control, establishing the conceptual foundation for systems that reason about both actual and unrealized possibilities.

반사실적 추론(Counterfactual Reasoning)은 단순히 실제로 무엇이 발생했는지를 관찰하거나 개입(Intervention)했을 때 무엇이 발생할지를 추정하는 것을 넘어 인과 분석(Causal Analysis)을 확장합니다. 이는 동일한 개인, 시스템 또는 상황에서 특정 조건이 달랐다면 어떤 일이 발생했을지를 질문합니다. 이러한 능력은 인과 지식(Causal Knowledge)을 현실과 실제로 관찰되지 않은 대안적 가능성(Alternative Possibilities)을 비교하는 추론 메커니즘으로 전환합니다.

반사실(Counterfactual)은 관찰된 변수(Observed Variables), 사건(Events), 행동(Actions), 결과(Outcomes)를 포함하는 사실적 세계(Factual World)에서 시작합니다. 이후 추론 과정에서는 적절한 배경 요인(Background Factors)을 일관되게 유지하면서 하나 이상의 조건을 변경한 대안적 세계(Alternative World)를 구성합니다. 그 결과를 실제 결과와 비교함으로써 대안적 원인, 의사결정, 실패, 기회 및 결과에 대해 추론할 수 있습니다.

이러한 형태의 추론은 일반적인 예측(Prediction)과 근본적으로 다릅니다. 예측 모델(Predictive Model)은 과거 데이터의 상관관계(Correlation)를 기반으로 결과의 확률을 추정할 수 있지만, 반사실적 추론은 특정 인과 요인(Causal Factor)이 변경되었을 때 결과가 어떻게 달라지는지를 질문합니다. 따라서 유용한 반사실적 추론(Counterfactual Inference)을 위해서는 입력과 출력 사이의 정확한 통계적 매핑뿐 아니라 인과 구조(Causal Structure)에 대한 지식이 필요합니다.

구조적 인과 모델(Structural Causal Model)은 반사실적 추론을 위한 엄밀한 기반을 제공합니다. 변수들은 인과 메커니즘(Causal Mechanism)을 나타내는 구조 방정식(Structural Equation)을 통해 연결되며, 외생 변수(Exogenous Variable)는 모델 내부에서 설명되지 않는 배경 조건을 표현합니다. 관찰된 상황을 이러한 배경 변수의 타당한 값과 연결한 후 인과 메커니즘을 수정하여 대안적 결과를 시뮬레이션할 수 있습니다.

일반적인 개념적 절차는 귀추(Abduction), 행동(Action), 예측(Prediction)으로 구성됩니다. 귀추 단계에서는 관찰된 증거를 이용하여 실제 상황을 만들어냈을 가능성이 있는 잠재적 배경 조건(Latent Background Conditions)을 추론합니다. 행동 단계에서는 가상 조건에 따라 선택된 인과관계를 변경합니다. 예측 단계에서는 수정된 인과 시스템(Causal System)을 평가하여 이에 대응하는 반사실적 결과(Counterfactual Outcome)를 결정합니다.

따라서 반사실적 추론은 연관(Association)이나 개입(Intervention)만을 사용하는 것보다 더 깊은 수준에서 작동합니다. 연관은 변수들이 함께 관찰될 때 무엇이 발생하는지를 질문하고, 개입은 특정 변수를 의도적으로 변경했을 때 무엇이 발생할 것으로 예상되는지를 질문합니다. 반사실적 추론은 특정한 실제 사례에 대해 이미 알려진 정보를 조건으로 추가함으로써 인과 메커니즘과 개별 상황을 연결합니다.

이러한 구분이 특히 중요한 이유는 동일한 사례에서 사실적 결과(Factual Outcome)와 반사실적 결과(Counterfactual Outcome)를 일반적으로 동시에 관찰할 수 없기 때문입니다. 로봇이 경로 A(Path A)를 선택했다면 정확히 동일한 상황에서 경로 B(Path B)를 선택했을 때 어떤 일이 발생했을지를 동시에 관찰할 수 없습니다. 따라서 반사실적 추론은 인과적 가정(Causal Assumptions), 구조적 지식(Structural Knowledge), 불확실성 모델링(Uncertainty Modeling), 실험적 증거(Experimental Evidence) 등을 이용하여 관찰되지 않은 대안을 재구성해야 합니다.

반사실적 질문(Counterfactual Question)은 행동, 환경 조건(Environmental Condition), 내부 상태(Internal State), 또는 인과 메커니즘 자체를 대상으로 할 수 있습니다. 엔지니어는 온도 상승이 없었다면 고장이 발생했을지를 질문할 수 있고, 의사는 치료가 없었을 경우의 결과를 고려할 수 있으며, 자율 에이전트(Autonomous Agent)는 다른 행동을 선택했다면 충돌을 피할 수 있었는지를 평가할 수 있습니다. 서로 다른 영역이지만 모두 관찰된 궤적(Observed Trajectory)을 인과적으로 수정된 대안과 비교한다는 공통점을 가집니다.

이러한 능력은 설명(Explanation)과도 밀접하게 관련됩니다. 두 변수가 상관관계를 가진다고 말하는 것만으로는 하나의 변수를 변경했을 때 결과를 방지할 수 있었다는 것을 입증할 수 없습니다. 더 강력한 설명은 의심되는 원인(Suspected Cause)을 제거하거나 변경했을 때 결과가 유지되는지를 평가합니다. 따라서 반사실적 의존성(Counterfactual Dependence)은 특정 사건에서 어떤 요인이 인과적으로 중요했는지를 식별하고 우연한 연관과 구별하는 데 도움을 줍니다.

반사실(Counterfactual)은 지능형 에이전트(Intelligent Agent)가 실제로 수행하지 않은 행동을 평가해야 한다는 점에서 의사결정(Decision Making)의 핵심 요소이기도 합니다. 결과를 관찰한 이후 에이전트는 다른 의사결정이 더 나은 결과를 만들어냈을지를 질문할 수 있습니다. 반복적인 반사실 평가(Counterfactual Evaluation)는 정책 개선(Policy Improvement), 후회 분석(Regret Analysis), 계획(Planning), 신용 할당(Credit Assignment), 제한된 경험으로부터의 학습을 지원합니다.

AI 설명가능성(AI Explainability)에서 반사실적 추론은 의미 있는 변화에 기반한 직관적인 설명 방법을 제공합니다. 단순히 특징 중요도(Feature Importance)를 보고하는 대신 어떤 조건이 변경되었다면 시스템의 결정이 달라졌을지를 설명할 수 있습니다. 예를 들어 반사실적 설명(Counterfactual Explanation)은 소수의 인과적으로 관련된 조건이 달랐다면 출력이 어떻게 변경되었을지를 보여줌으로써 모델의 행동을 보다 쉽게 검토하고 평가할 수 있도록 합니다.

로보틱스(Robotics)에서는 반사실적 추론이 인식--예측--행동 루프(Perception--Prediction--Action Loop)의 일부가 될 수 있습니다. 로봇은 현재 세계를 관찰하고 인과 상태(Causal State)를 추정한 후 후보 개입(Candidate Intervention)을 고려하고 대안적 미래 궤적(Alternative Future Trajectory)을 예측하여 예상 결과에 따라 행동을 선택할 수 있습니다. 실행 이후 예측 결과와 실제 결과 사이의 차이를 이용해 인과 모델을 개선함으로써 새로운 환경에서 계획과 적응 능력을 점진적으로 향상시킬 수 있습니다.

반사실 시뮬레이션(Counterfactual Simulation)은 실제 실험이 비싸거나 위험하거나 느리거나 되돌릴 수 없는 경우 특히 높은 가치를 가집니다. 산업 시스템은 장비를 실제로 변경하기 전에 대안적 운전 파라미터(Operating Parameter)를 검토할 수 있고, 자율주행 시스템은 충돌 회피 시나리오를 평가할 수 있으며, 과학 AI(Scientific AI)는 실제 실험을 수행하기 전에 가상의 메커니즘을 탐색할 수 있습니다. 이를 통해 불필요한 개입을 줄이면서 실제 실험을 보다 정보 가치가 높은 대안으로 집중할 수 있습니다.

그러나 반사실적 결론(Counterfactual Conclusion)의 신뢰성은 이를 뒷받침하는 인과적 가정의 신뢰성을 넘어설 수 없습니다. 잘못된 그래프 구조(Graph Structure), 누락된 교란 변수(Confounder), 부정확한 구조 방정식, 분포 이동(Distribution Shift), 부적절하게 모델링된 잠재 변수(Latent Variable)는 설득력 있어 보이지만 잘못된 대안 세계를 만들어낼 수 있습니다. 따라서 반사실 시스템은 대안적 시뮬레이션을 관찰된 사실처럼 취급하기보다 불확실성 추정(Uncertainty Estimation), 민감도 분석(Sensitivity Analysis), 인과 검증(Causal Validation), 명시적인 가정 관리가 필요합니다.

또 다른 중요한 과제는 사실적 세계에서 어떤 요소를 변경하지 않고 유지해야 하는지를 결정하는 것입니다. 비현실적인 반사실은 하나의 변수만 변경하면서 그 변수와 인과적으로 함께 변화해야 하는 다른 변수들을 무시할 수 있습니다. 효과적인 추론은 실행 가능성(Feasibility), 시간적 일관성(Temporal Consistency), 물리적 제약(Physical Constraints), 인과적 의존성(Causal Dependencies)을 준수하여 대안적 시나리오가 실제로 존재할 수 없는 임의의 변수 조합이 아니라 일관된 세계를 나타내도록 해야 합니다.

반사실적 추론은 월드 모델(World Model) 및 모델 기반 지능(Model-Based Intelligence)과도 자연스럽게 연결됩니다. 충분히 구조화된 월드 모델은 가능성이 높은 미래 상태만 표현하는 것이 아니라 서로 다른 행동과 인과적 변화에 따라 미래 상태가 어떻게 달라지는지도 표현해야 합니다. 이를 통해 지능형 시스템은 하나의 가장 가능성 높은 미래를 예측하는 수준에서 벗어나 서로 다른 의사결정, 개입 및 환경 조건으로부터 생성되는 여러 가능한 미래를 비교하고 평가할 수 있습니다.

따라서 인과성과 과학 AI(Causality and Scientific AI)의 전체 구조에서 반사실적 추론은 구조적 인과 지식(Structural Causal Knowledge)과 지능적 행동(Intelligent Action)을 연결하는 중요한 가교 역할을 합니다. 이 장에서는 가정적 추론(What-if Reasoning), 반사실 모델(Counterfactual Models), 개입(Intervention), 반사실 추정(Counterfactual Estimation), 인과 설명(Causal Explanation), 그리고 의사결정 시스템(Decision Systems), AI 설명가능성, 로봇 제어(Robotics Control) 응용으로 확장되며, 실제 가능성과 실현되지 않은 가능성을 함께 추론하는 지능형 시스템의 개념적 기반을 형성합니다.

##  

## 03.01. What if Reasoning

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

What-if reasoning is the process of exploring how an outcome might change when one or more conditions in a situation are hypothetically altered. Rather than accepting the observed world as the only possible trajectory, an intelligent system constructs alternative scenarios and asks how events would unfold under different assumptions, actions, environmental states, or causal mechanisms.

The central idea is to distinguish the factual situation from a hypothetical alternative. The factual world represents what actually occurred, while the hypothetical world changes selected conditions and preserves other relevant background factors as consistently as possible. The comparison between these two worlds provides information about how sensitive an outcome is to a particular decision, event, or causal factor.

What-if reasoning is broader than simple forecasting because it does not merely ask what is likely to happen next. Forecasting typically extrapolates from the current state and historical patterns, whereas what-if reasoning explicitly changes part of the assumed state or mechanism. It therefore supports questions such as what would happen if an action were delayed, a component failed, a resource became unavailable, or an environmental condition changed.

The usefulness of what-if reasoning depends on defining the hypothetical modification precisely. A vague question such as "what if the system were different?" does not specify which variables should change or which relationships should remain fixed. A meaningful scenario must identify the modified condition, the relevant causal dependencies, the time at which the change occurs, and the assumptions that define the alternative world.

In causal analysis, what-if reasoning can operate at different levels of strength. A simple scenario may change an input and observe how a predictive model responds, but this does not necessarily represent a valid causal alternative. Stronger reasoning modifies a variable according to a causal model so that downstream consequences follow the structural relationships that connect causes, intermediate states, and outcomes.

This distinction matters because correlated variables cannot always be changed independently. If one variable is causally determined by another, constructing an alternative state by modifying only one may produce an impossible or internally inconsistent scenario. Reliable what-if reasoning must therefore respect causal constraints, physical relationships, temporal ordering, and domain knowledge when generating hypothetical alternatives.

Structural causal models provide a natural framework for representing these dependencies. Variables are connected through causal mechanisms that describe how each state is generated from its causes. A hypothetical change can then be introduced into a selected mechanism or variable, after which the model propagates the resulting effects through the remaining causal structure to estimate a new outcome.

What-if reasoning is closely related to intervention reasoning, although the two concepts should not be treated as identical in every context. An intervention asks what happens when a variable is deliberately set to a value, while a broader what-if question may involve changes to actions, assumptions, mechanisms, resources, or environmental conditions. Counterfactual reasoning further specializes this process by conditioning the hypothetical alternative on a particular observed case.

Temporal structure is especially important in dynamic systems. Changing an event at one moment can alter later states, which in turn influence subsequent observations and decisions. In such systems, a what-if scenario is better represented as an alternative trajectory rather than a single modified data point, because the consequences of one change may accumulate and interact across multiple future time steps.

For decision systems, what-if reasoning provides a mechanism for evaluating actions before they are executed. An agent can generate candidate actions, predict their consequences, compare expected outcomes, and select the action that best satisfies its objective. This ability is fundamental to planning because most candidate actions must be evaluated without first performing them in the real environment.

After an action has already been taken, the same reasoning framework can support learning from alternatives. A system may examine whether another action could have produced a better result, whether an observed failure could have been avoided, or whether a different sequence of choices would have reduced cost or risk. Such analysis supports regret evaluation, policy refinement, and improved future decision making.

What-if reasoning is particularly valuable in robotics and autonomous systems because physical experimentation can be expensive or dangerous. A robot can evaluate alternative paths, velocities, control commands, grasp strategies, or interaction sequences inside a model before selecting an action. This reduces the need to test every alternative directly in the physical world and enables safer planning under uncertainty.

For example, an autonomous robot approaching an obstacle may consider several hypothetical futures. It can estimate the consequences of continuing forward, slowing down, stopping, or changing direction. Each alternative modifies the intended action while maintaining the current environmental context, allowing the robot to compare predicted trajectories and choose the option with the most acceptable safety and task outcome.

Engineering systems use similar reasoning for fault analysis and system design. Engineers may ask what would happen if a sensor failed, a structural load increased, a cooling system became less effective, or a control parameter changed. By examining the propagation of these hypothetical disturbances, the system can identify critical dependencies, vulnerable components, and possible mitigation strategies before an actual failure occurs.

What-if analysis is also useful in scientific reasoning because hypotheses often describe alternative mechanisms or conditions. A scientific AI system can compare predictions generated under competing explanations and determine which experiments would most effectively distinguish them. In this sense, hypothetical reasoning helps transform a model from a passive predictor into an active tool for designing informative experiments.

World models provide an important computational foundation for this capability in intelligent agents. A world model represents how states evolve under actions and environmental influences, allowing the system to internally simulate possible futures. What-if reasoning uses this internal model to create multiple hypothetical trajectories rather than committing immediately to one predicted future.

A stronger world model should support more than statistical continuation of observed patterns. It should represent which variables can be changed, which states are causally dependent, which transitions are physically possible, and how uncertainty propagates through alternative scenarios. These properties allow hypothetical simulation to remain consistent with the structure of the environment rather than generating merely plausible-looking futures.

Uncertainty remains unavoidable because hypothetical outcomes are not directly observed. Different causal structures, unknown latent factors, incomplete state estimation, and stochastic dynamics can produce different predictions from the same what-if question. Intelligent systems should therefore represent a range of possible outcomes or confidence levels rather than presenting every hypothetical simulation as a certain consequence.

The quality of what-if reasoning also depends on selecting useful alternatives. The number of imaginable scenarios can grow extremely large, making exhaustive simulation impractical. Effective systems must prioritize scenarios that are feasible, causally meaningful, relevant to the current objective, sufficiently different from the factual trajectory, or particularly informative for reducing uncertainty and improving decisions.

Another important requirement is minimal and interpretable change. In many applications, the most useful hypothetical scenario is not one that completely reconstructs the world but one that alters a small number of relevant factors. Such scenarios make it easier to understand why an outcome changes and help identify which decisions or conditions have the greatest causal influence on the result.

What-if reasoning therefore connects causal modeling, simulation, planning, explanation, and learning. It enables AI systems to explore alternatives without immediately acting on them, compare possible consequences, and use those comparisons to improve decisions. Within counterfactual reasoning, it forms the conceptual entry point for progressively more rigorous analysis of interventions, alternative outcomes, and causal explanations.

As AI systems become more autonomous, the ability to ask meaningful what-if questions becomes increasingly important. An intelligent system should not only recognize the current state and predict its most likely continuation, but also reason about how the future could change under different choices and conditions. This transition from passive prediction to structured alternative reasoning is a key step toward adaptable, causal, and decision-capable intelligence.

가정적 추론(What-if Reasoning)은 어떤 상황에서 하나 이상의 조건을 가상으로 변경했을 때 결과가 어떻게 달라질 수 있는지를 탐색하는 과정입니다. 지능형 시스템(Intelligent System)은 관찰된 세계를 유일하게 가능한 궤적(Trajectory)으로 받아들이는 대신 대안적 시나리오(Alternative Scenario)를 구성하고, 서로 다른 가정, 행동, 환경 상태 또는 인과 메커니즘(Causal Mechanism)에서 사건이 어떻게 전개될지를 질문합니다.

핵심 개념은 사실적 상황(Factual Situation)과 가상적 대안(Hypothetical Alternative)을 구분하는 것입니다. 사실적 세계(Factual World)는 실제로 발생한 것을 나타내는 반면, 가상적 세계(Hypothetical World)는 선택된 조건을 변경하면서 다른 관련 배경 요인(Background Factor)을 가능한 한 일관되게 유지합니다. 두 세계의 비교를 통해 특정 의사결정, 사건 또는 인과 요인(Causal Factor)에 따라 결과가 얼마나 민감하게 달라지는지를 파악할 수 있습니다.

가정적 추론은 단순한 예측(Forecasting)보다 더 넓은 개념입니다. 예측은 일반적으로 현재 상태와 과거 패턴을 바탕으로 앞으로 발생할 가능성이 높은 상황을 추정하지만, 가정적 추론은 가정된 상태나 메커니즘의 일부를 명시적으로 변경합니다. 따라서 행동이 지연된다면, 부품이 고장 난다면, 자원을 사용할 수 없게 된다면, 또는 환경 조건이 변한다면 어떤 일이 발생할지를 탐색할 수 있습니다.

가정적 추론의 유용성은 가상적 변경(Hypothetical Modification)을 얼마나 정확하게 정의하는지에 달려 있습니다. "시스템이 달랐다면 어떻게 되었을까?"와 같은 모호한 질문은 어떤 변수를 변경하고 어떤 관계를 유지해야 하는지 명확하지 않습니다. 의미 있는 시나리오를 구성하려면 변경되는 조건, 관련 인과 의존성(Causal Dependency), 변화가 발생하는 시점, 그리고 대안적 세계를 정의하는 가정을 구체적으로 설정해야 합니다.

인과 분석(Causal Analysis)에서 가정적 추론은 서로 다른 수준의 인과적 강도를 가질 수 있습니다. 단순한 시나리오는 입력을 변경한 뒤 예측 모델(Predictive Model)의 반응을 관찰할 수 있지만, 이것이 반드시 유효한 인과적 대안(Causal Alternative)을 의미하지는 않습니다. 보다 강한 추론은 인과 모델(Causal Model)에 따라 변수를 변경하여 원인, 중간 상태, 결과를 연결하는 구조적 관계를 통해 후속 결과가 발생하도록 합니다.

이러한 구분이 중요한 이유는 상관된 변수(Correlated Variable)를 항상 독립적으로 변경할 수 있는 것은 아니기 때문입니다. 하나의 변수가 다른 변수에 의해 인과적으로 결정된다면 특정 변수만 변경하여 만든 대안 상태는 불가능하거나 내부적으로 일관성이 없을 수 있습니다. 따라서 신뢰할 수 있는 가정적 추론은 가상적 대안을 생성할 때 인과적 제약(Causal Constraint), 물리적 관계, 시간적 순서(Temporal Ordering), 도메인 지식(Domain Knowledge)을 준수해야 합니다.

구조적 인과 모델(Structural Causal Model)은 이러한 의존성을 표현하기 위한 자연스러운 프레임워크를 제공합니다. 변수들은 각 상태가 원인으로부터 어떻게 생성되는지를 설명하는 인과 메커니즘을 통해 연결됩니다. 선택된 메커니즘이나 변수에 가상적 변화를 적용한 후 그 영향이 나머지 인과 구조(Causal Structure)를 통해 전파되도록 하여 새로운 결과를 추정할 수 있습니다.

가정적 추론은 개입 추론(Intervention Reasoning)과 밀접하게 관련되어 있지만 모든 상황에서 두 개념을 동일하게 취급해서는 안 됩니다. 개입은 변수를 특정 값으로 의도적으로 설정했을 때 무엇이 발생하는지를 질문하지만, 더 넓은 의미의 가정적 질문은 행동, 가정, 메커니즘, 자원 또는 환경 조건의 변화를 포함할 수 있습니다. 반사실적 추론(Counterfactual Reasoning)은 특정하게 관찰된 사례를 조건으로 가상적 대안을 구성함으로써 이러한 과정을 더욱 구체화합니다.

동적 시스템(Dynamic System)에서는 시간적 구조(Temporal Structure)가 특히 중요합니다. 특정 시점의 사건을 변경하면 이후 상태가 달라지고, 이러한 상태 변화는 다시 후속 관찰과 의사결정에 영향을 줄 수 있습니다. 따라서 이러한 시스템에서 가정적 시나리오는 하나의 수정된 데이터 포인트보다 대안적 궤적(Alternative Trajectory)으로 표현하는 것이 적절합니다. 하나의 변화가 여러 미래 시점에 걸쳐 누적되고 상호작용할 수 있기 때문입니다.

의사결정 시스템(Decision System)에서 가정적 추론은 행동을 실제로 실행하기 전에 평가하는 메커니즘을 제공합니다. 에이전트(Agent)는 후보 행동(Candidate Action)을 생성하고 그 결과를 예측하며 예상 결과를 비교한 뒤 자신의 목적을 가장 잘 만족시키는 행동을 선택할 수 있습니다. 대부분의 후보 행동은 실제 환경에서 먼저 수행하지 않고 평가해야 하므로 이러한 능력은 계획(Planning)의 핵심 기반이 됩니다.

행동이 이미 수행된 이후에도 동일한 추론 프레임워크를 활용하여 대안으로부터 학습할 수 있습니다. 시스템은 다른 행동이 더 좋은 결과를 만들었을지, 관찰된 실패를 피할 수 있었을지, 또는 다른 선택 순서가 비용이나 위험을 감소시켰을지를 검토할 수 있습니다. 이러한 분석은 후회 평가(Regret Evaluation), 정책 개선(Policy Refinement), 향상된 미래 의사결정을 지원합니다.

가정적 추론은 실제 실험이 비싸거나 위험할 수 있기 때문에 로보틱스(Robotics)와 자율 시스템(Autonomous System)에서 특히 중요합니다. 로봇은 행동을 선택하기 전에 모델 내부에서 대안적 경로, 속도, 제어 명령(Control Command), 파지 전략(Grasp Strategy), 상호작용 순서를 평가할 수 있습니다. 이를 통해 모든 대안을 실제 물리 세계에서 직접 시험할 필요성을 줄이고 불확실성하에서 더욱 안전한 계획을 수행할 수 있습니다.

예를 들어 장애물에 접근하는 자율 로봇(Autonomous Robot)은 여러 가상적 미래(Hypothetical Future)를 고려할 수 있습니다. 계속 전진하거나, 감속하거나, 정지하거나, 방향을 변경했을 때의 결과를 각각 추정할 수 있습니다. 각 대안은 현재 환경적 맥락(Environmental Context)을 유지하면서 의도된 행동을 변경하며, 이를 통해 로봇은 예측된 궤적들을 비교하고 안전성과 작업 수행 측면에서 가장 적절한 선택을 할 수 있습니다.

공학 시스템(Engineering System)에서도 고장 분석(Fault Analysis)과 시스템 설계를 위해 유사한 추론이 사용됩니다. 엔지니어는 센서가 고장 난다면, 구조 하중이 증가한다면, 냉각 시스템의 효율이 감소한다면, 또는 제어 파라미터(Control Parameter)가 변경된다면 어떤 일이 발생할지를 질문할 수 있습니다. 이러한 가상적 교란(Hypothetical Disturbance)의 전파를 분석하면 실제 고장이 발생하기 전에 핵심 의존성, 취약한 구성요소, 가능한 완화 전략(Mitigation Strategy)을 식별할 수 있습니다.

가정적 분석(What-if Analysis)은 가설(Hypothesis)이 대안적 메커니즘이나 조건을 설명하는 경우가 많기 때문에 과학적 추론(Scientific Reasoning)에서도 유용합니다. 과학 AI(Scientific AI) 시스템은 서로 경쟁하는 설명에서 생성된 예측을 비교하고 어떤 실험이 이들을 가장 효과적으로 구별할 수 있는지 판단할 수 있습니다. 이러한 의미에서 가상적 추론은 모델을 수동적인 예측기에서 정보 가치가 높은 실험을 설계하는 능동적 도구로 전환합니다.

월드 모델(World Model)은 지능형 에이전트에서 이러한 능력을 구현하기 위한 중요한 계산적 기반(Computational Foundation)을 제공합니다. 월드 모델은 행동과 환경적 영향에 따라 상태가 어떻게 변화하는지를 표현하여 시스템 내부에서 가능한 미래를 시뮬레이션할 수 있도록 합니다. 가정적 추론은 이러한 내부 모델을 이용하여 하나의 예측된 미래에 즉시 확정하지 않고 여러 가상적 궤적(Hypothetical Trajectory)을 생성합니다.

더 강력한 월드 모델은 관찰된 패턴을 통계적으로 연장하는 것 이상의 능력을 지원해야 합니다. 어떤 변수를 변경할 수 있는지, 어떤 상태가 인과적으로 의존하는지, 어떤 상태 전이(State Transition)가 물리적으로 가능한지, 그리고 불확실성(Uncertainty)이 대안적 시나리오를 통해 어떻게 전파되는지를 표현해야 합니다. 이를 통해 가상적 시뮬레이션이 단순히 그럴듯한 미래를 생성하는 것이 아니라 환경의 구조와 일관성을 유지할 수 있습니다.

가상적 결과는 직접 관찰되지 않기 때문에 불확실성을 완전히 제거할 수 없습니다. 서로 다른 인과 구조, 알려지지 않은 잠재 요인(Latent Factor), 불완전한 상태 추정(State Estimation), 확률적 동역학(Stochastic Dynamics)은 동일한 가정적 질문에서도 서로 다른 예측을 생성할 수 있습니다. 따라서 지능형 시스템은 모든 가상적 시뮬레이션을 확정된 결과로 제시하기보다 가능한 결과의 범위나 신뢰 수준(Confidence Level)을 표현해야 합니다.

가정적 추론의 품질은 유용한 대안(Useful Alternative)을 선택하는 능력에도 좌우됩니다. 상상할 수 있는 시나리오의 수는 매우 빠르게 증가할 수 있으므로 모든 경우를 시뮬레이션하는 것은 현실적으로 어렵습니다. 효과적인 시스템은 실행 가능하고, 인과적으로 의미가 있으며, 현재 목적과 관련되고, 실제 궤적과 충분히 다르거나, 불확실성을 감소시키고 의사결정을 개선하는 데 높은 정보 가치를 갖는 시나리오를 우선적으로 선택해야 합니다.

또 하나의 중요한 요구사항은 최소한의 해석 가능한 변화(Minimal and Interpretable Change)입니다. 많은 응용에서 가장 유용한 가상적 시나리오는 세계 전체를 완전히 재구성하는 것이 아니라 소수의 관련 요인만 변경하는 것입니다. 이러한 시나리오는 결과가 왜 달라지는지를 쉽게 이해할 수 있게 하며 어떤 의사결정이나 조건이 결과에 가장 큰 인과적 영향(Causal Influence)을 미치는지를 식별하는 데 도움을 줍니다.

따라서 가정적 추론은 인과 모델링(Causal Modeling), 시뮬레이션(Simulation), 계획, 설명, 학습을 서로 연결합니다. AI 시스템은 이를 통해 대안을 즉시 실행하지 않고도 탐색하고, 가능한 결과를 비교하며, 이러한 비교 결과를 이용하여 의사결정을 개선할 수 있습니다. 반사실적 추론에서 가정적 추론은 개입, 대안적 결과(Alternative Outcome), 인과 설명(Causal Explanation)에 대한 보다 엄밀한 분석으로 발전하기 위한 개념적 출발점 역할을 합니다.

AI 시스템의 자율성(Autonomy)이 높아질수록 의미 있는 가정적 질문을 생성하고 평가하는 능력은 더욱 중요해집니다. 지능형 시스템은 현재 상태를 인식하고 가장 가능성 높은 미래만 예측하는 데 그치지 않고, 서로 다른 선택과 조건에 따라 미래가 어떻게 달라질 수 있는지도 추론해야 합니다. 이러한 수동적 예측(Passive Prediction)에서 구조화된 대안적 추론(Structured Alternative Reasoning)으로의 전환은 적응 가능하고 인과적이며 의사결정 능력을 갖춘 지능으로 발전하기 위한 핵심 단계입니다.

##  

## 03.02. Counterfactual Models

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Counterfactual models provide a formal representation for reasoning about outcomes that did not actually occur but could have occurred under different conditions. They connect observed evidence with hypothetical alternatives by specifying how variables are causally generated and how those mechanisms would respond to changes. This makes counterfactual analysis more disciplined than unconstrained imagination or ordinary scenario generation.

The central problem addressed by a counterfactual model is that only one realized outcome can normally be observed for a particular situation. If an autonomous system chooses action A, the same physical episode cannot simultaneously reveal the outcome of action B. A counterfactual model represents this missing alternative mathematically or computationally, allowing the unrealized outcome to be estimated from causal assumptions and available evidence.

Structural causal models provide one of the most important foundations for constructing counterfactual models. A structural causal model represents variables through equations that specify how each endogenous variable is determined by its causal parents and exogenous background variables. These equations describe mechanisms rather than merely statistical associations, allowing selected mechanisms to be modified while the remainder of the causal system is preserved.

Exogenous variables play a particularly important role because they represent background conditions that are not explained by other variables inside the model. They may capture individual characteristics, environmental circumstances, disturbances, or latent factors. Counterfactual reasoning attempts to preserve background circumstances associated with the observed case while changing the specific variable or mechanism involved in the hypothetical question.

This preservation creates a connection between the factual and counterfactual worlds. Rather than generating an entirely independent alternative sample, the model asks what would happen to the same underlying case under a different causal condition. Shared background variables provide a form of identity across the two worlds, enabling meaningful comparison between what actually happened and what could have happened.

Counterfactual inference is commonly understood through the sequence of abduction, action, and prediction. Abduction uses observed evidence to infer plausible values or distributions for unobserved background variables. Action modifies the causal model according to the hypothetical condition. Prediction then propagates the modified causal mechanisms forward to calculate the outcome that would arise in the resulting counterfactual world.

During abduction, the model effectively reconstructs the hidden circumstances that may have produced the observed evidence. Because these circumstances are often uncertain, the result may be a probability distribution rather than a single state. Maintaining this uncertainty is important because several latent configurations may explain the same observations, and they may generate different outcomes after a hypothetical intervention.

The action stage creates the counterfactual change. A variable may be assigned a different value, an action may be replaced, or a causal mechanism may be altered according to the question being investigated. The modification must be distinguished from ordinary observation because changing a cause can break its original generating relationship and produce downstream consequences throughout the causal system.

Prediction evaluates the modified model while retaining the background information inferred from the factual case. Downstream variables are recomputed according to their structural equations, producing the hypothetical outcome. Comparing this result with the observed outcome reveals how the selected change could have affected the system and provides the basis for counterfactual explanation, decision analysis, and alternative-action evaluation.

Counterfactual models can represent deterministic or stochastic systems. In deterministic models, fixed background variables and a specified intervention determine a unique alternative outcome. In stochastic environments, multiple outcomes may remain possible because of uncertainty, noise, incomplete observations, or probabilistic dynamics. The model should therefore represent distributions over counterfactual outcomes when a single deterministic answer cannot be justified.

Temporal counterfactual models extend these ideas to sequences and dynamic systems. Instead of changing one isolated variable, they can modify an action or event at a particular time and simulate its effects across subsequent states. This is especially important for autonomous systems, where an early decision may alter later observations, opportunities, risks, and actions, producing an entirely different trajectory.

Counterfactual models are closely related to potential outcomes, but the two perspectives emphasize different representations. Potential-outcome reasoning describes outcomes associated with alternative treatments or actions, whereas structural models explicitly represent the mechanisms connecting variables. Both address unrealized alternatives, but structural representations can provide richer explanations of how changes propagate through intermediate causal relationships.

A critical requirement is counterfactual consistency. The hypothetical world should remain compatible with known facts except where changes are required by the counterfactual condition and its causal consequences. Arbitrarily modifying unrelated variables can produce an incoherent scenario. Good models therefore preserve relevant factual information while allowing causally downstream variables to respond naturally to the hypothetical modification.

Feasibility is equally important. A mathematically possible counterfactual may violate physical, biological, engineering, temporal, or operational constraints. Counterfactual models used in real systems should distinguish merely representable states from realistically achievable alternatives. This is particularly important when counterfactual results are used to recommend actions rather than simply explain past events.

For AI explainability, counterfactual models can identify changes that would have altered a model or system decision. Instead of reporting only that a variable was influential, the system can evaluate alternative values and determine whether the decision would change. Useful explanations generally favor small, understandable, actionable, and feasible modifications rather than unrealistic combinations of many simultaneous changes.

In decision systems, counterfactual models allow an agent to evaluate actions that were not selected. After observing the consequence of one action, the agent can estimate what alternative actions might have produced under comparable background conditions. This supports policy evaluation, regret estimation, credit assignment, offline learning, and improvement from historical experience without requiring every candidate decision to be executed.

Robotics provides a natural application because robots continuously interact with environments in which actions have physical consequences. A robot can reason about whether another velocity, path, grasp, or control command would have prevented a failure or improved task performance. Such models can combine state estimation, dynamics, causal structure, and simulation to reconstruct alternative trajectories from recorded episodes.

Counterfactual models can also contribute to failure analysis in engineering. After a system failure, the model can examine whether the outcome would still have occurred if a component had remained functional, a load had been smaller, or a control response had been different. This helps distinguish contributing factors from root causes and can guide redesign, maintenance strategies, and preventive control.

The reliability of counterfactual conclusions depends strongly on model identification and causal assumptions. Observational data alone may not determine every causal relationship or counterfactual quantity uniquely. Different structural models can sometimes explain the same observed distribution while implying different hypothetical outcomes, making experimental evidence, domain knowledge, assumptions, and sensitivity analysis essential components of responsible inference.

Latent confounding presents another challenge. If important common causes are missing, the model may attribute changes to the wrong mechanism and produce misleading alternatives. Measurement error, incomplete state representation, incorrect temporal ordering, and distribution shift can create similar problems. Counterfactual estimates should therefore be accompanied by uncertainty and by clear statements about assumptions that cannot be verified directly from available data.

Modern AI creates opportunities to combine counterfactual models with learned representations and world models. High-dimensional observations such as images, language, sensor streams, and robot states can be mapped into latent representations in which relevant causal factors are modeled. The challenge is to ensure that learned latent variables capture mechanisms that support interventions rather than only statistical features useful for prediction.

A causal world model can extend ordinary predictive simulation by representing how alternative interventions produce different future trajectories. Instead of asking only what will probably happen next, the system can ask what would happen under action A, action B, or a changed environmental condition. Counterfactual modeling therefore provides an important mechanism for turning internal simulation into structured causal reasoning.

Counterfactual models ultimately connect observed experience, causal structure, and unrealized possibilities within one reasoning framework. They enable intelligent systems to reconstruct alternative outcomes, explain events, evaluate unchosen actions, analyze failures, and improve future decisions. Within causal AI, they provide the formal bridge from general what-if reasoning toward rigorous intervention, counterfactual estimation, causal explanation, and autonomous decision making.

반사실 모델(Counterfactual Model)은 실제로 발생하지 않았지만 조건이 달랐다면 발생할 수 있었던 결과를 추론하기 위한 형식적 표현(Formal Representation)을 제공합니다. 이는 변수들이 인과적으로 어떻게 생성되는지와 조건 변화에 따라 그 메커니즘이 어떻게 반응하는지를 명시함으로써 관찰된 증거(Observed Evidence)와 가상적 대안(Hypothetical Alternative)을 연결합니다. 이를 통해 반사실 분석(Counterfactual Analysis)은 제약 없는 상상이나 일반적인 시나리오 생성보다 체계적으로 수행될 수 있습니다.

반사실 모델이 다루는 핵심 문제는 특정 상황에서 일반적으로 하나의 실현된 결과(Realized Outcome)만 관찰할 수 있다는 점입니다. 자율 시스템(Autonomous System)이 행동 A(Action A)를 선택하면 동일한 물리적 상황에서 행동 B(Action B)의 결과를 동시에 관찰할 수 없습니다. 반사실 모델은 이러한 관찰되지 않은 대안을 수학적 또는 계산적으로 표현하여 인과적 가정(Causal Assumption)과 이용 가능한 증거를 바탕으로 실현되지 않은 결과를 추정할 수 있도록 합니다.

구조적 인과 모델(Structural Causal Model)은 반사실 모델을 구성하는 가장 중요한 기반 가운데 하나입니다. 구조적 인과 모델은 각 내생 변수(Endogenous Variable)가 인과적 부모 변수(Causal Parent)와 외생 배경 변수(Exogenous Background Variable)에 의해 어떻게 결정되는지를 구조 방정식(Structural Equation)으로 표현합니다. 이러한 방정식은 단순한 통계적 연관이 아니라 메커니즘을 설명하므로 나머지 인과 시스템을 유지하면서 선택된 메커니즘을 변경할 수 있습니다.

외생 변수(Exogenous Variable)는 모델 내부의 다른 변수로 설명되지 않는 배경 조건(Background Condition)을 나타내기 때문에 특히 중요한 역할을 합니다. 여기에는 개별 특성, 환경적 상황, 외부 교란(Disturbance), 잠재 요인(Latent Factor) 등이 포함될 수 있습니다. 반사실적 추론(Counterfactual Reasoning)은 관찰된 사례와 관련된 이러한 배경 상황을 유지하면서 가상적 질문에서 지정한 변수나 메커니즘만 변경하려고 합니다.

이러한 배경 상황의 보존은 사실적 세계(Factual World)와 반사실적 세계(Counterfactual World)를 연결합니다. 모델은 완전히 독립적인 대안 표본을 생성하는 대신 동일한 근본적 사례가 서로 다른 인과 조건에 놓였다면 어떤 일이 발생했을지를 질문합니다. 공유된 배경 변수는 두 세계 사이의 동일성(Identity)을 유지하는 역할을 하며 실제로 발생한 결과와 발생할 수 있었던 결과를 의미 있게 비교할 수 있도록 합니다.

반사실 추론(Counterfactual Inference)은 일반적으로 귀추(Abduction), 행동(Action), 예측(Prediction)의 순서로 이해할 수 있습니다. 귀추는 관찰된 증거를 사용하여 관찰되지 않은 배경 변수의 가능한 값이나 분포를 추론합니다. 행동 단계에서는 가상적 조건에 따라 인과 모델을 변경합니다. 이후 예측 단계에서는 수정된 인과 메커니즘을 앞으로 전파하여 결과적으로 형성되는 반사실적 세계의 결과를 계산합니다.

귀추 단계에서 모델은 관찰된 증거를 발생시켰을 가능성이 있는 숨겨진 상황(Hidden Circumstance)을 사실상 재구성합니다. 이러한 상황에는 불확실성이 존재하는 경우가 많기 때문에 결과는 하나의 상태가 아니라 확률 분포(Probability Distribution)로 표현될 수 있습니다. 동일한 관찰을 여러 잠재 구성(Latent Configuration)이 설명할 수 있고 가상적 개입 이후 서로 다른 결과를 생성할 수 있으므로 이러한 불확실성을 유지하는 것이 중요합니다.

행동 단계에서는 반사실적 변화(Counterfactual Change)를 생성합니다. 조사하려는 질문에 따라 변수에 다른 값을 할당하거나, 기존 행동을 다른 행동으로 대체하거나, 인과 메커니즘 자체를 변경할 수 있습니다. 원인을 변경하면 기존의 생성 관계(Generating Relationship)가 단절되고 인과 시스템 전체에 걸쳐 하류 결과(Downstream Consequence)가 발생할 수 있으므로 이러한 변경은 단순한 관찰과 명확하게 구분되어야 합니다.

예측 단계에서는 사실적 사례에서 추론한 배경 정보를 유지하면서 수정된 모델을 평가합니다. 하류 변수(Downstream Variable)는 구조 방정식에 따라 다시 계산되며 이를 통해 가상적 결과(Hypothetical Outcome)가 생성됩니다. 이 결과를 관찰된 실제 결과와 비교하면 선택된 변화가 시스템에 어떤 영향을 미칠 수 있었는지를 파악할 수 있으며, 이는 반사실적 설명(Counterfactual Explanation), 의사결정 분석(Decision Analysis), 대안 행동 평가(Alternative-Action Evaluation)의 기반이 됩니다.

반사실 모델은 결정론적 시스템(Deterministic System)과 확률적 시스템(Stochastic System)을 모두 표현할 수 있습니다. 결정론적 모델에서는 배경 변수가 고정되고 개입이 지정되면 하나의 대안적 결과가 결정됩니다. 확률적 환경에서는 불확실성, 잡음, 불완전한 관찰 또는 확률적 동역학(Probabilistic Dynamics)으로 인해 여러 결과가 가능하므로 단일한 결정론적 답을 정당화할 수 없다면 반사실 결과의 분포를 표현해야 합니다.

시간적 반사실 모델(Temporal Counterfactual Model)은 이러한 개념을 시퀀스(Sequence)와 동적 시스템(Dynamic System)으로 확장합니다. 하나의 고립된 변수를 변경하는 대신 특정 시점의 행동이나 사건을 변경하고 이후 상태 전체에 미치는 영향을 시뮬레이션할 수 있습니다. 초기 의사결정이 이후의 관찰, 기회, 위험, 행동을 변화시켜 완전히 다른 궤적(Trajectory)을 만들어낼 수 있는 자율 시스템에서는 이러한 접근이 특히 중요합니다.

반사실 모델은 잠재 결과(Potential Outcomes)와 밀접하게 관련되어 있지만 두 관점은 서로 다른 표현을 강조합니다. 잠재 결과 접근법(Potential Outcomes Approach)은 대안적 처치(Treatment)나 행동에 대응하는 결과를 기술하는 반면 구조적 모델(Structural Model)은 변수들을 연결하는 메커니즘을 명시적으로 표현합니다. 두 접근 모두 실현되지 않은 대안을 다루지만 구조적 표현은 변화가 중간 인과관계를 통해 어떻게 전파되는지에 대해 더욱 풍부한 설명을 제공할 수 있습니다.

중요한 요구사항 가운데 하나는 반사실적 일관성(Counterfactual Consistency)입니다. 가상적 세계는 반사실 조건과 그에 따른 인과적 결과로 인해 반드시 변경되어야 하는 부분을 제외하고 알려진 사실과 일관성을 유지해야 합니다. 관련 없는 변수를 임의로 변경하면 일관되지 않은 시나리오가 만들어질 수 있으므로 좋은 모델은 관련된 사실적 정보를 유지하면서 인과적으로 하류에 위치한 변수들이 가상적 변경에 자연스럽게 반응하도록 해야 합니다.

실행 가능성(Feasibility)도 마찬가지로 중요합니다. 수학적으로 가능한 반사실이 물리적, 생물학적, 공학적, 시간적 또는 운영적 제약을 위반할 수 있습니다. 실제 시스템에서 사용하는 반사실 모델은 단순히 표현 가능한 상태와 현실적으로 달성 가능한 대안을 구분해야 합니다. 반사실 결과가 과거 사건을 설명하는 것에 그치지 않고 실제 행동을 추천하는 데 사용될 경우 이러한 구분은 더욱 중요합니다.

AI 설명가능성(AI Explainability)에서 반사실 모델은 어떤 변화가 모델이나 시스템의 결정을 변경했을지를 식별할 수 있습니다. 단순히 특정 변수가 영향력이 있었다고 보고하는 대신 시스템은 대안적 값을 평가하고 결정이 실제로 변경되는지를 판단할 수 있습니다. 유용한 설명은 일반적으로 많은 변수를 동시에 비현실적으로 변경하기보다 작고 이해하기 쉬우며 실행 가능하고 현실적인 변화(Actionable and Feasible Change)를 선호합니다.

의사결정 시스템(Decision System)에서 반사실 모델은 에이전트가 선택하지 않았던 행동을 평가할 수 있도록 합니다. 하나의 행동 결과를 관찰한 이후 에이전트는 동일하거나 비교 가능한 배경 조건에서 다른 행동이 어떤 결과를 만들었을지를 추정할 수 있습니다. 이는 정책 평가(Policy Evaluation), 후회 추정(Regret Estimation), 신용 할당(Credit Assignment), 오프라인 학습(Offline Learning), 과거 경험을 통한 정책 개선을 지원합니다.

로보틱스(Robotics)는 로봇의 행동이 물리적 결과를 발생시키는 환경과 지속적으로 상호작용하기 때문에 반사실 모델을 자연스럽게 적용할 수 있는 영역입니다. 로봇은 다른 속도, 경로, 파지(Grasp), 제어 명령(Control Command)을 사용했다면 실패를 방지하거나 작업 성능을 향상시킬 수 있었는지를 추론할 수 있습니다. 이러한 모델은 상태 추정(State Estimation), 동역학(Dynamics), 인과 구조, 시뮬레이션을 결합하여 기록된 에피소드로부터 대안적 궤적을 재구성할 수 있습니다.

반사실 모델은 공학 분야의 고장 분석(Failure Analysis)에도 기여할 수 있습니다. 시스템 고장 이후 특정 부품이 정상적으로 작동했다면, 하중이 더 작았다면, 또는 제어 응답이 달랐다면 동일한 결과가 발생했을지를 분석할 수 있습니다. 이를 통해 단순한 기여 요인(Contributing Factor)과 근본 원인(Root Cause)을 구분하고 시스템 재설계, 유지보수 전략(Maintenance Strategy), 예방 제어(Preventive Control)를 수립하는 데 활용할 수 있습니다.

반사실적 결론의 신뢰성은 모델 식별(Model Identification)과 인과적 가정에 크게 의존합니다. 관찰 데이터(Observational Data)만으로 모든 인과관계나 반사실적 수량(Counterfactual Quantity)을 유일하게 결정할 수 있는 것은 아닙니다. 서로 다른 구조적 모델이 동일한 관찰 분포를 설명하면서 서로 다른 가상적 결과를 제시할 수도 있으므로 실험적 증거, 도메인 지식, 명시적인 가정, 민감도 분석(Sensitivity Analysis)이 책임 있는 추론의 핵심 요소가 됩니다.

잠재적 교란(Latent Confounding) 역시 중요한 문제입니다. 중요한 공통 원인(Common Cause)이 누락되면 모델은 변화를 잘못된 메커니즘에 귀속하여 오해를 일으키는 대안을 생성할 수 있습니다. 측정 오류(Measurement Error), 불완전한 상태 표현, 잘못된 시간적 순서, 분포 이동(Distribution Shift)도 유사한 문제를 만들 수 있습니다. 따라서 반사실 추정에는 불확실성과 이용 가능한 데이터만으로 직접 검증할 수 없는 가정에 대한 명확한 설명이 함께 제공되어야 합니다.

현대 AI(Modern AI)는 반사실 모델을 학습된 표현(Learned Representation) 및 월드 모델(World Model)과 결합할 수 있는 가능성을 제공합니다. 이미지, 언어, 센서 스트림(Sensor Stream), 로봇 상태와 같은 고차원 관찰(High-Dimensional Observation)을 관련된 인과 요인을 모델링할 수 있는 잠재 표현(Latent Representation)으로 변환할 수 있습니다. 핵심 과제는 학습된 잠재 변수가 단순히 예측에 유용한 통계적 특징이 아니라 개입을 지원하는 인과 메커니즘을 포착하도록 만드는 것입니다.

인과 월드 모델(Causal World Model)은 대안적 개입이 서로 다른 미래 궤적을 어떻게 생성하는지를 표현함으로써 일반적인 예측 시뮬레이션(Predictive Simulation)을 확장할 수 있습니다. 시스템은 단순히 다음에 무엇이 발생할 가능성이 높은지를 질문하는 대신 행동 A, 행동 B 또는 변경된 환경 조건에서 어떤 일이 발생할지를 질문할 수 있습니다. 따라서 반사실 모델링은 내부 시뮬레이션(Internal Simulation)을 구조화된 인과 추론(Structured Causal Reasoning)으로 전환하는 중요한 메커니즘을 제공합니다.

궁극적으로 반사실 모델은 관찰된 경험(Observed Experience), 인과 구조(Causal Structure), 실현되지 않은 가능성(Unrealized Possibility)을 하나의 추론 프레임워크 안에서 연결합니다. 이를 통해 지능형 시스템은 대안적 결과를 재구성하고, 사건을 설명하고, 선택하지 않은 행동을 평가하며, 실패를 분석하고, 미래의 의사결정을 개선할 수 있습니다. 인과 AI(Causal AI)에서 반사실 모델은 일반적인 가정적 추론(What-if Reasoning)을 엄밀한 개입(Intervention), 반사실 추정(Counterfactual Estimation), 인과 설명(Causal Explanation), 자율적 의사결정(Autonomous Decision Making)으로 연결하는 형식적 가교 역할을 합니다.

##  

## 03.03. Intervention and Do Operator

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Intervention is a central concept in causal reasoning because it distinguishes actively changing a system from merely observing it. When a variable is observed to have a particular value, its value may reflect many upstream causes. When the same variable is deliberately set through an intervention, its ordinary causal generation mechanism is replaced, allowing the consequences of that controlled change to be studied separately from observational associations.

The do-operator provides a formal notation for expressing interventions. The expression do(X = x) means that variable X is externally forced to take value x rather than receiving its value through its normal causal parents. This operation represents a modification of the causal system itself, making it fundamentally different from simply conditioning on the observation X = x in a probability distribution.

This distinction can be expressed through the difference between P(Y \| X = x) and P(Y \| do(X = x)). The first quantity describes the distribution of Y among cases where X is observed to equal x, while the second describes the distribution of Y when X is deliberately set to x. These quantities may coincide under suitable conditions, but confounding or selection mechanisms can cause them to differ substantially.

A structural causal model makes the meaning of intervention especially clear. Suppose X is normally generated by a structural equation using its causal parents and an exogenous variable. Under do(X = x), this structural equation is replaced by the constant assignment X := x. The remaining structural equations stay unchanged, allowing the effects of the intervention to propagate through descendants of X according to the model\'s causal mechanisms.

Graphically, an intervention can be represented by modifying the causal graph associated with the model. When do(X = x) is applied, incoming causal edges from the parents of X are removed because those variables no longer determine X. Outgoing edges from X remain, since X can still influence its descendants. The resulting modified graph represents the causal system under the intervention rather than the original observational system.

This graph modification explains why intervention can separate causation from correlation. If a common cause Z influences both X and Y, observing X may provide information about Z and therefore about Y even when X has no direct causal effect on Y. Intervening on X breaks the normal influence of its parents, allowing changes in Y to be attributed more directly to causal pathways originating from X.

Confounding is therefore one of the main reasons the do-operator is needed. Observational data may contain statistical relationships produced by common causes rather than direct causal influence. Causal inference attempts to determine whether an interventional quantity can be estimated despite these relationships. When appropriate variables are measured, adjustment methods can sometimes reconstruct the effect of intervention from observational data.

A familiar example is treatment analysis. Patients receiving a treatment may differ systematically from untreated patients because age, disease severity, behavior, or other factors influence treatment selection. Comparing the two observed groups directly may therefore produce a biased estimate. The causal question instead asks what the outcome distribution would be if treatment status were externally assigned, corresponding conceptually to an interventional distribution.

Randomized experiments approximate this intervention by assigning treatment independently of many pre-existing causes. Randomization reduces systematic dependence between treatment assignment and confounding variables, making causal effects easier to estimate. However, experiments may be expensive, dangerous, unethical, or impossible, which motivates methods for identifying interventional effects from observational evidence combined with causal assumptions.

The backdoor criterion provides an important graphical principle for identifying causal effects. A set of variables can sometimes be conditioned on to block noncausal paths entering the treatment variable through its causal ancestors. If an appropriate adjustment set satisfies the required graphical conditions, observational quantities can be combined to estimate the distribution that would have resulted from an intervention.

Not every causal effect can be recovered through ordinary adjustment. Some causal structures contain mediators, latent confounders, selection effects, or other relationships requiring more sophisticated reasoning. The front-door criterion provides one important example in which a measured mediator can sometimes support identification even when the treatment and outcome are affected by an unobserved confounder.

Do-calculus generalizes these ideas by providing formal rules for transforming expressions containing interventions and observations. Its purpose is to determine whether a causal query involving do-operators can be rewritten using quantities available from observed or experimental distributions. This makes do-calculus an important theoretical bridge between assumptions encoded in causal graphs and quantities that can actually be estimated from data.

Intervention can target more than one variable. Expressions such as do(X = x, Z = z) represent simultaneous manipulations in which multiple generating mechanisms are replaced. Such interventions are useful for reasoning about coordinated policies, system configurations, robot actions, or experimental settings. Their effects must still be evaluated according to the remaining causal structure after the specified mechanisms have been modified.

Interventions may also be understood at different levels of realism. A perfect intervention completely overrides the normal mechanism generating a variable, while softer interventions can alter a mechanism without fixing its output to one constant value. Real systems often resemble soft interventions because control policies, environmental changes, or parameter adjustments modify probability distributions or mechanisms rather than deterministically assigning exact states.

Temporal interventions are especially important in dynamic systems. Applying an action at time t can modify the state at t+1, which then influences later observations, actions, and outcomes. Intervention reasoning must therefore consider how causal effects propagate through time. Repeated interventions create action-conditioned trajectories and provide a natural connection between causal inference, sequential decision making, control, and planning.

In robotics, the distinction between observation and intervention is fundamental because robots continuously act upon their environments. Observing that an object occupies a location differs from moving it there, just as observing low velocity differs from commanding the robot to slow down. Robot actions alter the causal state of the environment and therefore should be modeled as interventions when reasoning about their consequences.

A robot equipped with a causal world model can use interventions to evaluate candidate actions before physical execution. It may simulate do(turn = left), do(speed = low), or alternative manipulation commands and compare the resulting trajectories. This enables planning to move beyond statistical continuation of past observations toward explicit reasoning about how deliberate actions can change future states.

Intervention reasoning also supports failure analysis and diagnosis. An engineer may ask whether a failure would disappear if a particular component were replaced, a control parameter changed, or an environmental disturbance removed. By representing these modifications as interventions, the analysis can distinguish factors that merely correlate with failure from mechanisms whose manipulation would actually change the outcome.

The relationship between intervention and counterfactual reasoning is close but conceptually distinct. Intervention generally asks what would happen across a population or system if a variable were deliberately changed. Counterfactual reasoning additionally conditions the hypothetical intervention on evidence about a particular realized case, asking what would have happened in that same case under a different intervention.

This distinction corresponds to progressively richer levels of causal reasoning. Association concerns patterns in observations, intervention concerns consequences of deliberate changes, and counterfactual reasoning concerns alternative outcomes for specific observed situations. The do-operator provides the formal language for the intervention level and also becomes an essential component when constructing more advanced counterfactual queries.

Reliable intervention analysis depends on the correctness of the assumed causal model. Missing confounders, incorrect edge directions, measurement errors, interference between units, distribution shifts, or unrealistic intervention assumptions can invalidate causal estimates. The notation do(X = x) does not itself guarantee causality; it defines a causal query whose answer remains dependent on structural assumptions and available evidence.

For intelligent systems, the importance of intervention extends beyond estimating isolated causal effects. Autonomous agents must understand which aspects of the world they can manipulate, how actions propagate through causal mechanisms, and which consequences remain uncertain. Combining intervention models with perception, world models, simulation, planning, and learning enables AI to reason about actions as mechanisms for deliberately transforming future states.

Intervention and the do-operator therefore provide a formal transition from passive observation to active causal reasoning. They clarify the difference between seeing a condition and creating it, provide a mathematical language for controlled changes, and support identification of causal effects from experiments or observational evidence. Within counterfactual reasoning, this framework establishes the mechanism through which hypothetical actions modify causal worlds and generate alternative outcomes.

개입(Intervention)은 시스템을 단순히 관찰하는 것과 시스템을 능동적으로 변화시키는 것을 구분하기 때문에 인과 추론(Causal Reasoning)의 핵심 개념입니다. 어떤 변수가 특정 값을 갖는 것을 관찰했을 때 그 값은 여러 상위 원인(Upstream Cause)의 영향을 반영할 수 있습니다. 반면 동일한 변수를 개입을 통해 의도적으로 설정하면 일반적인 인과적 생성 메커니즘(Causal Generation Mechanism)이 대체되며, 이를 통해 통계적 연관과 분리하여 통제된 변화의 결과를 분석할 수 있습니다.

두 연산자(Do-Operator)는 개입을 표현하기 위한 형식적 표기법(Formal Notation)을 제공합니다. do(X = x)라는 표현은 변수 X가 정상적인 인과적 부모(Causal Parent)를 통해 값을 전달받는 대신 외부에서 강제로 x라는 값을 갖도록 설정된다는 의미입니다. 이러한 연산은 인과 시스템(Causal System) 자체의 수정을 나타내기 때문에 단순히 확률 분포에서 X = x라는 관찰 조건을 부여하는 것과 근본적으로 다릅니다.

이러한 차이는 P(Y \| X = x)와 P(Y \| do(X = x))의 차이로 표현할 수 있습니다. 첫 번째 값은 X가 x로 관찰된 사례에서 Y의 분포를 나타내는 반면, 두 번째 값은 X를 의도적으로 x로 설정했을 때 Y의 분포를 나타냅니다. 특정 조건에서는 두 값이 동일할 수 있지만 교란(Confounding)이나 선택 메커니즘(Selection Mechanism)이 존재하면 상당한 차이가 발생할 수 있습니다.

구조적 인과 모델(Structural Causal Model)은 개입의 의미를 특히 명확하게 보여줍니다. X가 일반적으로 인과적 부모와 외생 변수(Exogenous Variable)를 이용하는 구조 방정식(Structural Equation)에 의해 생성된다고 가정해 보겠습니다. do(X = x)를 적용하면 이 구조 방정식은 상수 할당 X := x로 대체됩니다. 나머지 구조 방정식은 변경되지 않으므로 개입의 효과가 모델의 인과 메커니즘에 따라 X의 후손 변수(Descendant Variable)로 전파됩니다.

그래프 관점에서 개입은 모델과 연결된 인과 그래프(Causal Graph)를 수정하는 것으로 표현할 수 있습니다. do(X = x)가 적용되면 X의 부모로부터 들어오는 인과적 간선(Incoming Causal Edge)이 제거됩니다. 해당 변수들이 더 이상 X를 결정하지 않기 때문입니다. 반면 X에서 나가는 간선(Outgoing Edge)은 유지되며 X는 여전히 후손 변수에 영향을 줄 수 있습니다. 이렇게 수정된 그래프는 원래의 관찰 시스템이 아니라 개입이 적용된 인과 시스템을 나타냅니다.

이러한 그래프 수정은 개입을 통해 인과관계(Causation)와 상관관계(Correlation)를 구분할 수 있는 이유를 설명합니다. 공통 원인(Common Cause) Z가 X와 Y 모두에 영향을 준다면 X를 관찰하는 것은 Z에 대한 정보를 제공하고, X가 Y에 직접적인 인과 효과를 갖지 않더라도 Y에 대한 정보를 제공할 수 있습니다. X에 개입하면 부모 변수의 정상적인 영향이 차단되어 Y의 변화를 X에서 시작되는 인과 경로에 보다 직접적으로 연결할 수 있습니다.

따라서 교란(Confounding)은 두 연산자가 필요한 주요 이유 가운데 하나입니다. 관찰 데이터(Observational Data)에는 직접적인 인과 영향이 아니라 공통 원인에 의해 발생한 통계적 관계가 포함될 수 있습니다. 인과 추론(Causal Inference)은 이러한 관계가 존재하더라도 개입적 수량(Interventional Quantity)을 추정할 수 있는지를 판단합니다. 적절한 변수들이 측정되어 있다면 조정 방법(Adjustment Method)을 이용하여 관찰 데이터로부터 개입 효과를 재구성할 수 있습니다.

대표적인 예는 처치 분석(Treatment Analysis)입니다. 치료를 받은 환자는 연령, 질병의 심각도, 행동 또는 기타 요인이 치료 선택에 영향을 미치기 때문에 치료를 받지 않은 환자와 체계적으로 다를 수 있습니다. 따라서 관찰된 두 집단을 직접 비교하면 편향된 추정(Biased Estimate)이 발생할 수 있습니다. 인과적 질문은 대신 치료 상태를 외부에서 할당했을 경우 결과 분포가 어떻게 달라지는지를 묻고 있으며, 이는 개념적으로 개입 분포(Interventional Distribution)에 해당합니다.

무작위 실험(Randomized Experiment)은 처치를 기존의 여러 원인과 독립적으로 할당함으로써 이러한 개입을 근사합니다. 무작위화(Randomization)는 처치 할당과 교란 변수 사이의 체계적인 의존성을 감소시켜 인과 효과(Causal Effect)를 보다 쉽게 추정할 수 있도록 합니다. 그러나 실험은 비용이 많이 들거나 위험하거나 윤리적으로 문제가 있거나 수행 자체가 불가능할 수 있으므로 인과적 가정과 관찰 증거를 결합하여 개입 효과를 식별하는 방법이 필요합니다.

백도어 기준(Backdoor Criterion)은 인과 효과를 식별하기 위한 중요한 그래프 원리(Graphical Principle)를 제공합니다. 특정 변수 집합을 조건으로 사용하여 처치 변수의 인과적 선행 변수(Causal Ancestor)를 통해 들어오는 비인과적 경로(Noncausal Path)를 차단할 수 있습니다. 적절한 조정 집합(Adjustment Set)이 필요한 그래프 조건을 만족한다면 관찰 데이터의 확률적 수량을 결합하여 개입으로 발생했을 분포를 추정할 수 있습니다.

모든 인과 효과를 일반적인 조정만으로 복원할 수 있는 것은 아닙니다. 일부 인과 구조에는 매개 변수(Mediator), 잠재 교란 변수(Latent Confounder), 선택 효과(Selection Effect) 또는 보다 복잡한 추론을 요구하는 관계가 존재합니다. 프런트도어 기준(Front-Door Criterion)은 처치와 결과가 관찰되지 않은 교란 변수의 영향을 받더라도 측정된 매개 변수를 이용하여 특정 조건에서 인과 효과를 식별할 수 있는 중요한 사례를 제공합니다.

두 계산(Do-Calculus)은 개입과 관찰을 포함하는 표현을 변환하기 위한 형식적 규칙(Formal Rule)을 제공함으로써 이러한 개념을 일반화합니다. 두 계산의 목적은 두 연산자를 포함하는 인과적 질의(Causal Query)를 관찰 또는 실험 분포에서 얻을 수 있는 수량으로 변환할 수 있는지를 판단하는 것입니다. 따라서 두 계산은 인과 그래프에 표현된 가정과 실제 데이터에서 추정할 수 있는 수량을 연결하는 중요한 이론적 가교 역할을 합니다.

개입은 하나 이상의 변수를 동시에 대상으로 할 수도 있습니다. do(X = x, Z = z)와 같은 표현은 여러 변수의 생성 메커니즘을 동시에 대체하는 조작을 나타냅니다. 이러한 개입은 서로 연계된 정책(Policy), 시스템 구성(System Configuration), 로봇 행동(Robot Action), 실험 조건 등을 추론하는 데 유용합니다. 개입의 효과는 지정된 메커니즘이 변경된 이후에도 남아 있는 인과 구조에 따라 평가되어야 합니다.

개입은 현실성의 수준에 따라서도 구분할 수 있습니다. 완전 개입(Perfect Intervention)은 변수를 생성하는 정상적인 메커니즘을 완전히 덮어쓰는 반면, 소프트 개입(Soft Intervention)은 출력값을 하나의 상수로 고정하지 않고 메커니즘 자체를 변화시킬 수 있습니다. 실제 시스템에서는 제어 정책, 환경 변화 또는 파라미터 조정이 정확한 상태를 결정론적으로 할당하기보다 확률 분포나 메커니즘을 변화시키는 경우가 많기 때문에 소프트 개입에 가까운 경우가 많습니다.

시간적 개입(Temporal Intervention)은 동적 시스템(Dynamic System)에서 특히 중요합니다. 시간 t에서 행동을 적용하면 t+1의 상태가 변경되고, 이는 다시 이후의 관찰, 행동, 결과에 영향을 줄 수 있습니다. 따라서 개입 추론은 인과 효과가 시간에 따라 어떻게 전파되는지를 고려해야 합니다. 반복적인 개입은 행동 조건부 궤적(Action-Conditioned Trajectory)을 생성하며 인과 추론, 순차적 의사결정(Sequential Decision Making), 제어(Control), 계획(Planning)을 자연스럽게 연결합니다.

로보틱스(Robotics)에서는 로봇이 지속적으로 환경에 행동을 가하기 때문에 관찰과 개입의 구분이 근본적으로 중요합니다. 물체가 특정 위치에 존재하는 것을 관찰하는 것과 로봇이 그 물체를 해당 위치로 이동시키는 것은 서로 다릅니다. 마찬가지로 낮은 속도를 관찰하는 것과 로봇에게 감속 명령을 내리는 것도 다릅니다. 로봇의 행동은 환경의 인과 상태(Causal State)를 변화시키므로 그 결과를 추론할 때 개입으로 모델링해야 합니다.

인과 월드 모델(Causal World Model)을 갖춘 로봇은 실제 행동을 수행하기 전에 개입을 이용하여 후보 행동(Candidate Action)을 평가할 수 있습니다. 예를 들어 do(turn = left), do(speed = low) 또는 여러 대안적 조작 명령을 내부적으로 시뮬레이션하고 그 결과로 나타나는 궤적을 비교할 수 있습니다. 이를 통해 계획은 과거 관찰을 통계적으로 연장하는 수준을 넘어 의도적인 행동이 미래 상태를 어떻게 변화시키는지 명시적으로 추론하는 방향으로 발전합니다.

개입 추론(Intervention Reasoning)은 고장 분석(Failure Analysis)과 진단(Diagnosis)에도 활용됩니다. 엔지니어는 특정 부품을 교체하거나, 제어 파라미터를 변경하거나, 환경적 교란을 제거했을 때 고장이 사라지는지를 질문할 수 있습니다. 이러한 변화를 개입으로 표현하면 단순히 고장과 상관관계를 갖는 요인과 실제로 조작했을 때 결과를 변화시키는 메커니즘을 구분할 수 있습니다.

개입과 반사실적 추론(Counterfactual Reasoning)은 밀접하게 관련되어 있지만 개념적으로 구분됩니다. 개입은 일반적으로 특정 변수를 의도적으로 변경했을 때 모집단이나 시스템에서 어떤 일이 발생하는지를 질문합니다. 반사실적 추론은 여기에 특정하게 실현된 사례의 증거를 추가로 조건화하여 동일한 사례에 다른 개입을 적용했다면 어떤 일이 발생했을지를 질문합니다.

이러한 차이는 점차 풍부해지는 인과 추론의 수준(Level of Causal Reasoning)에 대응합니다. 연관(Association)은 관찰된 데이터의 패턴을 다루고, 개입은 의도적인 변화의 결과를 다루며, 반사실적 추론은 특정 관찰 상황에서의 대안적 결과를 다룹니다. 두 연산자는 개입 수준을 표현하기 위한 형식적 언어를 제공하며 더욱 발전된 반사실적 질의(Counterfactual Query)를 구성할 때에도 핵심적인 요소가 됩니다.

신뢰할 수 있는 개입 분석은 가정된 인과 모델의 정확성에 의존합니다. 누락된 교란 변수(Missing Confounder), 잘못된 간선 방향(Edge Direction), 측정 오류(Measurement Error), 개체 간 간섭(Interference), 분포 이동(Distribution Shift), 비현실적인 개입 가정은 인과 추정을 무효화할 수 있습니다. do(X = x)라는 표기 자체가 인과성을 보장하는 것은 아니며, 구조적 가정과 이용 가능한 증거에 의존하는 인과적 질문을 정의하는 것입니다.

지능형 시스템(Intelligent System)에서 개입의 중요성은 개별적인 인과 효과를 추정하는 것보다 훨씬 넓습니다. 자율 에이전트(Autonomous Agent)는 세계의 어떤 부분을 조작할 수 있는지, 행동이 인과 메커니즘을 통해 어떻게 전파되는지, 어떤 결과에 불확실성이 남아 있는지를 이해해야 합니다. 개입 모델을 인식(Perception), 월드 모델(World Model), 시뮬레이션, 계획, 학습과 결합하면 AI가 행동을 미래 상태를 의도적으로 변화시키는 메커니즘으로 추론할 수 있습니다.

따라서 개입과 두 연산자(Intervention and Do-Operator)는 수동적 관찰(Passive Observation)에서 능동적 인과 추론(Active Causal Reasoning)으로 전환하기 위한 형식적 기반을 제공합니다. 이들은 어떤 조건을 관찰하는 것과 그 조건을 직접 만들어내는 것의 차이를 명확히 하고, 통제된 변화를 표현하는 수학적 언어를 제공하며, 실험 또는 관찰 증거로부터 인과 효과를 식별하도록 지원합니다. 반사실적 추론에서 이 프레임워크는 가상적 행동이 인과적 세계를 변경하고 대안적 결과를 생성하는 메커니즘을 확립합니다.

##  

## 03.04. Counterfactual Estimation [w/Code]

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Counterfactual estimation is the process of estimating outcomes that were not observed for a particular individual, system, or event. Because only one factual outcome is realized, the corresponding alternative outcome is fundamentally missing. The objective is therefore to infer this unobserved result from causal assumptions, observed evidence, structural models, experimental data, or combinations of these sources.

The fundamental difficulty is often called the fundamental problem of causal inference. For the same unit at the same moment, it is impossible to observe both the outcome under the factual action and the outcome under an alternative action. Counterfactual estimation attempts to reconstruct this missing quantity while preserving the characteristics and background conditions that define the original case.

In the potential outcomes framework, each unit is associated conceptually with multiple possible outcomes corresponding to different treatments or actions. If treatment T can take values 0 or 1, the outcomes may be written as Y(0) and Y(1). Only one is observed, while the other becomes the counterfactual outcome. Their difference represents an individual treatment effect that cannot normally be measured directly.

Population-level causal effects can nevertheless become estimable by combining information across comparable units. Quantities such as the Average Treatment Effect summarize expected differences between potential outcomes across a population. Counterfactual estimation at the individual level is generally more demanding because it requires stronger information about how the specific observed case would have behaved under another condition.

Structural causal models provide another framework for estimating counterfactuals. Observed evidence is first used to infer plausible background variables through abduction. The causal model is then modified according to the hypothetical intervention, and the resulting equations are evaluated to predict the alternative outcome. This procedure maintains a connection between the factual and counterfactual worlds through shared latent circumstances.

The quality of estimation depends strongly on whether the causal effect is identifiable. Identification asks whether a counterfactual or interventional quantity can be uniquely determined from the available data under specified causal assumptions. If multiple causal models are compatible with the observed data but imply different counterfactual outcomes, additional assumptions, experiments, or measurements are required.

Confounding is a major obstacle because treatment or action selection may depend on variables that also affect the outcome. Directly comparing treated and untreated observations can therefore produce biased estimates. Adjustment strategies attempt to make groups comparable with respect to relevant confounders so that differences in outcomes better approximate the consequences of changing the treatment itself.

Regression adjustment estimates outcomes as functions of treatments and observed covariates, allowing the model to predict what each unit might experience under alternative treatment values. The same individual can then be evaluated under multiple hypothetical conditions. However, reliable estimation requires adequate model specification and sufficient overlap between the observed treatment groups.

Propensity score methods approach the same problem from the treatment-assignment side. A propensity score estimates the probability that a unit receives a treatment given its observed characteristics. Matching, weighting, or stratifying observations according to these probabilities can construct more comparable populations and reduce bias caused by measured confounding.

Inverse probability weighting assigns larger weights to observations whose received treatments were relatively unlikely given their characteristics. The resulting weighted sample can approximate a pseudo-population in which treatment is less dependent on measured confounders. Counterfactual expectations can then be estimated by comparing outcomes across these reweighted treatment conditions.

Doubly robust estimation combines an outcome model with a treatment-assignment model. The estimator can remain consistent when either the outcome model or the propensity model is correctly specified under appropriate assumptions. This combination is attractive in practical causal analysis because it reduces dependence on the correctness of a single modeling component.

Matching methods estimate counterfactual outcomes by finding observations with similar relevant characteristics but different treatments or actions. The observed outcome of a sufficiently comparable unit can serve as an approximation to the missing outcome. Matching is intuitive, but its reliability decreases when high-dimensional covariates make genuinely comparable observations difficult to find.

Overlap, also called positivity, is essential for many estimation methods. For each relevant combination of characteristics, there must be meaningful probability of observing the alternative treatments being compared. If certain individuals always receive only one treatment, the data contain little direct evidence about what would happen to those individuals under another treatment.

Consistency provides another important assumption. It connects the observed outcome with the potential outcome corresponding to the treatment actually received. If a unit receives treatment T = 1, its observed outcome should correspond to Y(1). This apparently simple relationship becomes difficult when treatments are poorly defined, have multiple versions, or interact with contextual factors.

Unobserved confounding remains particularly challenging. Statistical adjustment can only control variables that have been measured or otherwise represented. If hidden factors influence both treatment and outcome, counterfactual estimates may remain biased even after sophisticated modeling. Sensitivity analysis is therefore important for examining how strongly an unobserved confounder would need to act to change the conclusion.

Machine learning can improve counterfactual estimation when outcomes depend on complex nonlinear relationships or high-dimensional covariates. Tree ensembles, neural networks, representation learning, and specialized causal learning architectures can estimate heterogeneous effects across populations. Their predictive flexibility is useful, but high predictive accuracy alone does not guarantee valid causal estimation.

Representation learning can attempt to construct latent spaces in which treated and untreated populations become more comparable while retaining information relevant to outcomes. This is especially useful when inputs include images, sensor data, language, or other complex observations. The central challenge is ensuring that the representation preserves causal factors instead of merely compressing statistical correlations.

Counterfactual uncertainty should be estimated whenever possible because the hypothetical outcome is never directly observed for validation in the same case. Uncertainty may originate from finite data, measurement noise, model parameters, latent variables, causal structure, or stochastic dynamics. Reliable systems should therefore provide distributions, intervals, or calibrated confidence rather than unsupported point estimates.

Evaluation of counterfactual estimators is difficult because ground-truth individual counterfactuals are typically unavailable in observational datasets. Randomized experiments, semi-synthetic datasets, simulators, and fully synthetic causal systems are therefore useful for benchmarking. These environments provide known treatment mechanisms or potential outcomes against which estimation errors can be measured.

Temporal counterfactual estimation extends the problem from isolated treatments to sequences of decisions. An alternative action at one time may change subsequent states, observations, available actions, and future rewards. Estimation must therefore reconstruct an entire alternative trajectory rather than predict one missing value, creating strong connections with sequential causal inference and reinforcement learning.

In robotics, counterfactual estimation can analyze recorded episodes to determine whether alternative actions might have prevented failures or improved performance. A robot may estimate outcomes under different velocities, paths, grasp configurations, or control commands. Combining causal models with dynamics and world models allows alternative trajectories to be evaluated without physically replaying every possibility.

Counterfactual estimation is also valuable for explainable AI. Instead of reporting only which variables influenced a prediction, a system can estimate how the outcome or decision would change under feasible modifications. Effective explanations usually favor minimal, actionable alternatives whose estimated effects are both causally meaningful and accompanied by uncertainty.

Ultimately, counterfactual estimation converts hypothetical reasoning into measurable causal quantities. It combines assumptions about causal structure with observational or experimental evidence to reconstruct missing outcomes, compare alternative actions, and quantify possible effects. Within counterfactual reasoning, it provides the computational bridge from asking what might have happened to estimating how different the alternative outcome could actually have been.

반사실 추정(Counterfactual Estimation)은 특정 개인, 시스템 또는 사건에서 실제로 관찰되지 않은 결과를 추정하는 과정입니다. 하나의 사실적 결과(Factual Outcome)만 실제로 실현되기 때문에 이에 대응하는 대안적 결과(Alternative Outcome)는 본질적으로 관찰되지 않습니다. 따라서 인과적 가정(Causal Assumption), 관찰된 증거(Observed Evidence), 구조적 모델(Structural Model), 실험 데이터(Experimental Data) 또는 이들의 조합을 이용하여 이러한 미관찰 결과를 추론하는 것이 목적입니다.

이러한 문제의 근본적인 어려움은 흔히 인과 추론의 근본적 문제(Fundamental Problem of Causal Inference)라고 불립니다. 동일한 개체(Unit)의 동일한 시점에서 사실적 행동에 따른 결과와 대안적 행동에 따른 결과를 동시에 관찰하는 것은 불가능합니다. 반사실 추정은 원래 사례를 정의하는 특성과 배경 조건(Background Condition)을 유지하면서 이렇게 누락된 결과를 재구성하려고 합니다.

잠재 결과 프레임워크(Potential Outcomes Framework)에서는 각각의 개체가 서로 다른 처치(Treatment) 또는 행동에 대응하는 여러 개의 가능한 결과를 개념적으로 가진다고 봅니다. 처치 T가 0 또는 1의 값을 갖는다면 결과는 Y(0)과 Y(1)로 표현할 수 있습니다. 이 가운데 하나만 관찰되고 다른 하나는 반사실 결과(Counterfactual Outcome)가 됩니다. 두 결과의 차이는 일반적으로 직접 측정할 수 없는 개별 처치 효과(Individual Treatment Effect)를 나타냅니다.

그러나 모집단 수준의 인과 효과(Population-Level Causal Effect)는 서로 비교 가능한 개체들의 정보를 결합함으로써 추정 가능해질 수 있습니다. 평균 처치 효과(Average Treatment Effect)와 같은 수량은 모집단 전체에서 잠재 결과 사이의 기대 차이를 요약합니다. 개별 수준의 반사실 추정은 특정 관찰 사례가 다른 조건에서 어떻게 행동했을지에 대한 더 강한 정보가 필요하기 때문에 일반적으로 더욱 어렵습니다.

구조적 인과 모델(Structural Causal Model)은 반사실을 추정하기 위한 또 다른 프레임워크를 제공합니다. 먼저 관찰된 증거를 사용하여 귀추(Abduction)를 통해 가능한 배경 변수를 추론합니다. 이후 가상적 개입(Hypothetical Intervention)에 따라 인과 모델을 수정하고, 수정된 방정식을 평가하여 대안적 결과를 예측합니다. 이 과정은 공유된 잠재적 상황(Shared Latent Circumstance)을 통해 사실적 세계(Factual World)와 반사실적 세계(Counterfactual World)의 연결을 유지합니다.

추정의 품질은 인과 효과가 식별 가능(Identifiable)한지 여부에 크게 좌우됩니다. 식별(Identification)은 명시된 인과적 가정 아래에서 이용 가능한 데이터로부터 반사실적 또는 개입적 수량(Interventional Quantity)을 유일하게 결정할 수 있는지를 묻습니다. 여러 인과 모델이 동일한 관찰 데이터와 일치하면서 서로 다른 반사실 결과를 제시한다면 추가적인 가정, 실험 또는 측정이 필요합니다.

교란(Confounding)은 처치나 행동의 선택이 결과에도 영향을 주는 변수에 의존할 수 있기 때문에 중요한 장애 요소입니다. 따라서 처치 집단과 비처치 집단의 관찰 결과를 직접 비교하면 편향된 추정(Biased Estimation)이 발생할 수 있습니다. 조정 전략(Adjustment Strategy)은 관련 교란 변수에 대해 집단들을 비교 가능한 상태로 만들어 결과의 차이가 처치 자체를 변경했을 때의 효과에 더욱 가깝도록 합니다.

회귀 조정(Regression Adjustment)은 처치와 관찰된 공변량(Covariate)의 함수로 결과를 추정하여 각 개체가 대안적인 처치 값을 받았을 때 어떤 결과를 경험할지를 예측합니다. 이를 통해 동일한 개인을 여러 가상적 조건에서 평가할 수 있습니다. 그러나 신뢰할 수 있는 추정을 위해서는 적절한 모델 명세(Model Specification)와 관찰된 처치 집단 사이의 충분한 중첩(Overlap)이 필요합니다.

성향 점수 방법(Propensity Score Method)은 동일한 문제를 처치 할당(Treatment Assignment)의 관점에서 접근합니다. 성향 점수(Propensity Score)는 관찰된 특성이 주어졌을 때 특정 개체가 처치를 받을 확률을 추정합니다. 이러한 확률에 따라 관찰 사례를 매칭(Matching), 가중(Weighting), 층화(Stratification)하면 서로 더욱 비교 가능한 모집단을 구성하고 측정된 교란으로 인한 편향을 감소시킬 수 있습니다.

역확률 가중법(Inverse Probability Weighting)은 개체의 특성을 고려했을 때 실제로 받은 처치의 확률이 상대적으로 낮은 관찰 사례에 더 큰 가중치를 부여합니다. 이렇게 구성된 가중 표본(Weighted Sample)은 처치가 측정된 교란 변수에 덜 의존하는 의사 모집단(Pseudo-Population)을 근사할 수 있습니다. 이후 재가중된 처치 조건 사이의 결과를 비교하여 반사실적 기대값을 추정할 수 있습니다.

이중 강건 추정(Doubly Robust Estimation)은 결과 모델(Outcome Model)과 처치 할당 모델(Treatment-Assignment Model)을 결합합니다. 적절한 가정 아래에서 결과 모델 또는 성향 모델 가운데 하나가 올바르게 명세되어 있다면 추정량이 일관성을 유지할 수 있습니다. 이러한 결합은 하나의 모델링 구성요소가 반드시 정확해야 한다는 의존성을 줄여준다는 점에서 실제 인과 분석에서 유용합니다.

매칭 방법(Matching Method)은 관련 특성이 유사하면서 서로 다른 처치나 행동을 받은 관찰 사례를 찾아 반사실 결과를 추정합니다. 충분히 비교 가능한 다른 개체의 관찰 결과를 누락된 결과에 대한 근사치로 사용할 수 있습니다. 매칭은 직관적인 방법이지만 고차원 공변량(High-Dimensional Covariate)으로 인해 실제로 비교 가능한 관찰 사례를 찾기 어려워질수록 신뢰성이 감소할 수 있습니다.

중첩(Overlap)은 양성성(Positivity)이라고도 하며 많은 추정 방법에서 필수적인 조건입니다. 관련 특성의 각 조합에 대해 비교하려는 대안적 처치가 관찰될 의미 있는 확률이 존재해야 합니다. 특정 특성을 가진 개인이 항상 하나의 처치만 받는다면 데이터에는 해당 개인이 다른 처치를 받았을 때 어떤 일이 발생할지를 판단할 직접적인 증거가 거의 존재하지 않습니다.

일관성(Consistency) 역시 중요한 가정입니다. 이는 관찰된 결과를 실제로 받은 처치에 대응하는 잠재 결과와 연결합니다. 어떤 개체가 처치 T = 1을 받았다면 관찰된 결과는 Y(1)에 대응해야 합니다. 겉보기에는 단순한 관계이지만 처치가 명확하게 정의되지 않았거나 여러 형태의 처치가 존재하거나 맥락적 요인(Contextual Factor)과 상호작용하는 경우에는 이러한 관계가 복잡해질 수 있습니다.

관찰되지 않은 교란(Unobserved Confounding)은 특히 어려운 문제로 남아 있습니다. 통계적 조정은 측정되거나 다른 방식으로 표현된 변수만 통제할 수 있습니다. 숨겨진 요인이 처치와 결과 모두에 영향을 준다면 정교한 모델링을 사용하더라도 반사실 추정에는 편향이 남을 수 있습니다. 따라서 관찰되지 않은 교란 요인이 어느 정도 강해야 결론이 달라질 수 있는지를 분석하는 민감도 분석(Sensitivity Analysis)이 중요합니다.

머신러닝(Machine Learning)은 결과가 복잡한 비선형 관계(Nonlinear Relationship)나 고차원 공변량에 의존할 때 반사실 추정을 향상시킬 수 있습니다. 트리 앙상블(Tree Ensemble), 신경망(Neural Network), 표현 학습(Representation Learning), 특화된 인과 학습 구조(Causal Learning Architecture)를 이용하여 모집단에 따라 달라지는 이질적 효과(Heterogeneous Effect)를 추정할 수 있습니다. 그러나 높은 예측 정확도만으로 유효한 인과 추정이 보장되는 것은 아닙니다.

표현 학습은 결과에 관련된 정보를 유지하면서 처치 집단과 비처치 집단을 보다 비교 가능한 상태로 만드는 잠재 공간(Latent Space)을 구성할 수 있습니다. 이는 입력이 이미지, 센서 데이터, 언어 또는 기타 복잡한 관찰로 구성될 때 특히 유용합니다. 핵심 과제는 표현이 단순히 통계적 상관관계를 압축하는 것이 아니라 인과적으로 중요한 요인(Causal Factor)을 보존하도록 만드는 것입니다.

반사실 결과는 동일한 사례에서 직접 관찰하여 검증할 수 없기 때문에 가능한 경우 반사실 불확실성(Counterfactual Uncertainty)을 함께 추정해야 합니다. 불확실성은 제한된 데이터, 측정 잡음(Measurement Noise), 모델 파라미터, 잠재 변수(Latent Variable), 인과 구조 또는 확률적 동역학(Stochastic Dynamics)에서 발생할 수 있습니다. 따라서 신뢰할 수 있는 시스템은 근거가 부족한 단일 점 추정(Point Estimate)보다 분포, 구간 또는 보정된 신뢰도(Calibrated Confidence)를 제공해야 합니다.

관찰 데이터셋(Observational Dataset)에서는 실제 개별 반사실 결과(Ground-Truth Individual Counterfactual)를 일반적으로 알 수 없기 때문에 반사실 추정기를 평가하는 것도 어렵습니다. 따라서 무작위 실험(Randomized Experiment), 준합성 데이터셋(Semi-Synthetic Dataset), 시뮬레이터(Simulator), 완전 합성 인과 시스템(Synthetic Causal System)이 벤치마킹에 유용합니다. 이러한 환경에서는 알려진 처치 메커니즘이나 잠재 결과를 이용하여 추정 오차를 측정할 수 있습니다.

시간적 반사실 추정(Temporal Counterfactual Estimation)은 문제를 개별적인 처치에서 일련의 의사결정으로 확장합니다. 한 시점에서 대안적 행동을 선택하면 이후 상태, 관찰, 이용 가능한 행동, 미래 보상(Future Reward)이 모두 달라질 수 있습니다. 따라서 하나의 누락된 값을 예측하는 것이 아니라 전체 대안적 궤적(Alternative Trajectory)을 재구성해야 하며, 이는 순차적 인과 추론(Sequential Causal Inference) 및 강화학습(Reinforcement Learning)과 강하게 연결됩니다.

로보틱스(Robotics)에서 반사실 추정은 기록된 에피소드(Recorded Episode)를 분석하여 대안적 행동이 실패를 방지하거나 성능을 향상시킬 수 있었는지를 판단하는 데 활용할 수 있습니다. 로봇은 서로 다른 속도, 경로, 파지 구성(Grasp Configuration), 제어 명령(Control Command)에 따른 결과를 추정할 수 있습니다. 인과 모델을 동역학(Dynamics) 및 월드 모델(World Model)과 결합하면 모든 가능성을 실제로 다시 실행하지 않고도 대안적 궤적을 평가할 수 있습니다.

반사실 추정은 설명가능한 AI(Explainable AI)에서도 중요한 가치를 가집니다. 단순히 어떤 변수가 예측에 영향을 주었는지를 보고하는 대신 실행 가능한 변경(Feasible Modification)을 적용했을 때 결과나 의사결정이 어떻게 달라지는지를 추정할 수 있습니다. 효과적인 설명은 일반적으로 최소한의 실행 가능한 대안(Minimal Actionable Alternative)을 선호하며, 그 추정 효과는 인과적으로 의미가 있어야 하고 불확실성 정보와 함께 제공되어야 합니다.

궁극적으로 반사실 추정은 가상적 추론(Hypothetical Reasoning)을 측정 가능한 인과적 수량(Measurable Causal Quantity)으로 전환합니다. 인과 구조에 대한 가정과 관찰 또는 실험 증거를 결합하여 누락된 결과를 재구성하고, 대안적 행동을 비교하며, 가능한 효과의 크기를 정량화합니다. 반사실적 추론(Counterfactual Reasoning)에서 이는 "어떤 일이 발생할 수도 있었는가?"라는 질문을 넘어 "대안적 결과가 실제 결과와 어느 정도 달라졌을 것인가?"를 추정하는 계산적 가교(Computational Bridge)를 제공합니다.

##  

## 03.05. Causal Explanation

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal explanation seeks to answer not only what happened, but why it happened in terms of underlying causal relationships. Within counterfactual reasoning, an explanation becomes stronger when it identifies factors whose alteration would have changed the observed outcome. This moves explanation beyond descriptive correlation toward claims about mechanisms, interventions, and alternative possibilities.

A descriptive explanation may identify variables that frequently appear together, but such associations do not establish that one variable produced another. Causal explanation requires a model of how changes propagate through a system. It therefore depends on distinguishing causes from consequences, identifying relevant intermediate variables, and recognizing background conditions that may influence both the proposed cause and the outcome.

Structural causal models provide a natural representation for causal explanations. Variables are connected through directed relationships, while structural equations describe how each variable is generated from its causal parents and exogenous influences. An explanation can then identify which pathways transmit causal influence and how modifying one component would alter downstream states while other mechanisms remain unchanged.

Counterfactual reasoning strengthens this framework by asking whether the outcome would still have occurred if a suspected cause had been different. If removing or changing a factor causes the modeled outcome to disappear, the factor may contribute causally to the event. If the outcome remains essentially unchanged, the factor may be correlated with the event without being necessary for its occurrence.

Causal explanation is therefore closely related to necessity and sufficiency. A cause may be necessary when the outcome would not have occurred without it, while another factor may be sufficient when its presence can generate the outcome under relevant conditions. Real systems frequently involve multiple interacting causes, so explanations often need to represent combinations of conditions rather than identify one isolated factor.

The distinction between direct and indirect causes is also important. A variable can affect an outcome through an intermediate mediator rather than through a direct causal edge. A useful explanation should distinguish the initiating cause, intermediate mechanisms, and final effect. This provides more insight than simply ranking correlated variables according to predictive importance.

Confounding complicates causal explanation because a common cause can make two variables appear related even when neither directly causes the other. If an explanation ignores such confounders, it may incorrectly attribute responsibility to an observed variable. Causal graphs and adjustment methods help determine whether an apparent relationship survives after relevant noncausal pathways are considered.

Intervention provides another test of explanatory claims. If changing X through do(X = x) systematically changes Y, this supports the interpretation that X lies on a causal pathway to Y under the assumed model. Observing X = x alone is weaker evidence because the observation may contain information about upstream variables that also influence Y.

Counterfactual explanations are especially useful for explaining individual cases. Rather than reporting only an average causal effect across a population, the system can ask what would have needed to change for the specific observed outcome to be different. This makes the explanation directly connected to the factual case while preserving the background conditions inferred for that case.

In explainable AI, this approach can produce explanations such as identifying the smallest feasible change that would alter a decision. Such explanations are often easier to interpret than large collections of feature-importance scores because they describe an alternative that has a clear consequence. However, the suggested modification should be causally valid, realistic, and actionable rather than merely statistically convenient.

Minimality is often desirable because explanations involving a small number of meaningful changes are easier to understand. Yet the smallest mathematical change is not always the best causal explanation. A useful explanation must also respect causal dependencies, temporal ordering, feasibility constraints, and the distinction between variables that can be manipulated and variables that merely describe a state.

Causal explanations can also be contrastive. Instead of asking only "Why did Y occur?", a user may ask "Why did Y occur rather than Y′?" The relevant explanation depends on this contrast because different causal factors may distinguish different alternative outcomes. Counterfactual models naturally support this form of reasoning by comparing the factual outcome with a specified alternative.

In engineering and failure analysis, causal explanation helps separate symptoms, contributing factors, and root causes. A component may correlate with a failure because both are consequences of another hidden problem. By testing counterfactual interventions such as replacing a component, reducing a load, or modifying control logic, the analysis can identify which mechanisms would actually prevent recurrence.

Robotics provides similar examples because a failed action often results from interacting perception, planning, control, environment, and dynamics. A robot can examine whether a different path, velocity, grasp, or state estimate would have changed the outcome. Such explanations can support debugging, policy improvement, safer operation, and learning from previously recorded episodes.

Causal explanation is also important for scientific AI because scientific understanding requires more than prediction. A model that predicts an event accurately may still fail to explain which mechanism produced it. By comparing alternative causal structures, interventions, and counterfactual outcomes, scientific systems can evaluate competing hypotheses and identify experiments that distinguish between them.

Uncertainty must remain visible in causal explanations. Different causal models may fit the same observational data while supporting different explanations, especially when important variables are latent or poorly measured. A responsible explanation should therefore reflect uncertainty about causal structure, parameter values, counterfactual outcomes, and assumptions rather than presenting one narrative as unquestionably true.

Explanation quality also depends on the intended user and purpose. An engineer may need a mechanistic explanation describing failure propagation, while a decision maker may need an actionable intervention and an AI user may need a concise contrastive explanation. The causal model can remain the same while the explanatory presentation selects different pathways, variables, and counterfactual comparisons.

World models can extend causal explanation into dynamic environments by representing how actions and states evolve over time. Instead of explaining only a static outcome, the system can identify which earlier action or state transition altered the later trajectory. Counterfactual simulation can then replay alternative trajectories and reveal how different interventions would have changed subsequent events.

For autonomous intelligence, causal explanation can become part of the learning loop rather than a separate reporting function. After observing an outcome, the system can reconstruct relevant causes, test alternative actions, compare counterfactual trajectories, and update its internal causal model. Explanation then contributes directly to adaptation, planning, diagnosis, and policy improvement.

Within the structure of counterfactual reasoning, causal explanation connects what-if reasoning, counterfactual models, interventions, and counterfactual estimation into an interpretable account of why outcomes occur. It transforms causal computations into structured explanations of mechanisms and alternatives, providing the conceptual bridge toward applications in decision systems, AI explainability, and robotics control.

인과 설명(Causal Explanation)은 단순히 무엇이 발생했는지를 밝히는 것을 넘어, 그 사건이 근본적인 인과관계(Causal Relationship)에 의해 왜 발생했는지를 설명하는 것을 목표로 합니다. 반사실적 추론(Counterfactual Reasoning)에서는 특정 요인을 변경했을 때 관찰된 결과도 달라졌을 것임을 식별할 수 있을 때 설명이 더욱 강력해집니다. 이를 통해 설명은 기술적 상관관계(Descriptive Correlation)를 넘어 메커니즘, 개입(Intervention), 대안적 가능성(Alternative Possibility)에 관한 주장으로 발전합니다.

기술적 설명(Descriptive Explanation)은 함께 자주 나타나는 변수들을 식별할 수 있지만, 이러한 연관성(Association)만으로 하나의 변수가 다른 변수를 발생시켰다고 판단할 수는 없습니다. 인과 설명에는 변화가 시스템을 통해 어떻게 전파되는지를 나타내는 모델이 필요합니다. 따라서 원인과 결과를 구분하고, 관련 중간 변수(Intermediate Variable)를 식별하며, 제안된 원인과 결과 모두에 영향을 줄 수 있는 배경 조건(Background Condition)을 인식해야 합니다.

구조적 인과 모델(Structural Causal Model)은 인과 설명을 위한 자연스러운 표현 방법을 제공합니다. 변수들은 방향성을 가진 관계(Directed Relationship)를 통해 연결되고, 구조 방정식(Structural Equation)은 각각의 변수가 인과적 부모(Causal Parent)와 외생적 영향(Exogenous Influence)으로부터 어떻게 생성되는지를 설명합니다. 이를 통해 어떤 경로가 인과적 영향을 전달하며 하나의 구성요소를 변경했을 때 다른 메커니즘을 유지하면서 하류 상태(Downstream State)가 어떻게 변화하는지를 설명할 수 있습니다.

반사실적 추론은 의심되는 원인(Suspected Cause)이 달랐더라도 결과가 여전히 발생했을지를 질문함으로써 이러한 프레임워크를 강화합니다. 특정 요인을 제거하거나 변경했을 때 모델링된 결과가 사라진다면 해당 요인은 사건에 인과적으로 기여했을 가능성이 있습니다. 반대로 결과가 거의 변하지 않는다면 해당 요인은 사건과 상관되어 있을 수 있지만 사건 발생에 반드시 필요한 원인은 아닐 수 있습니다.

따라서 인과 설명은 필요성(Necessity) 및 충분성(Sufficiency)과 밀접하게 관련됩니다. 어떤 원인이 없었다면 결과가 발생하지 않았을 경우 그 원인은 필요 조건(Necessary Condition)이 될 수 있으며, 특정 조건에서 어떤 요인의 존재만으로 결과를 발생시킬 수 있다면 충분 조건(Sufficient Condition)이 될 수 있습니다. 실제 시스템에서는 여러 원인이 상호작용하는 경우가 많으므로 하나의 독립된 요인보다 여러 조건의 조합을 설명해야 하는 경우가 많습니다.

직접 원인(Direct Cause)과 간접 원인(Indirect Cause)의 구분도 중요합니다. 하나의 변수는 직접적인 인과 간선(Causal Edge)이 아니라 중간의 매개 변수(Mediator)를 통해 결과에 영향을 미칠 수 있습니다. 유용한 설명은 최초 원인(Initiating Cause), 중간 메커니즘(Intermediate Mechanism), 최종 효과(Final Effect)를 구분해야 합니다. 이는 단순히 예측 중요도(Predictive Importance)에 따라 상관된 변수의 순위를 나열하는 것보다 더 깊은 통찰을 제공합니다.

교란(Confounding)은 공통 원인(Common Cause)이 두 변수를 직접적인 인과관계가 없는 상황에서도 서로 관련되어 보이도록 만들 수 있기 때문에 인과 설명을 어렵게 합니다. 이러한 교란 변수를 무시하면 관찰된 변수에 잘못된 인과적 책임을 부여할 수 있습니다. 인과 그래프(Causal Graph)와 조정 방법(Adjustment Method)은 관련된 비인과적 경로(Noncausal Path)를 고려한 이후에도 겉으로 나타난 관계가 유지되는지를 판단하는 데 도움을 줍니다.

개입(Intervention)은 설명적 주장(Explanatory Claim)을 검증하는 또 하나의 방법을 제공합니다. do(X = x)를 통해 X를 변경했을 때 Y가 체계적으로 변화한다면, 가정된 모델 아래에서 X가 Y로 이어지는 인과 경로(Causal Pathway)에 존재한다는 해석을 뒷받침합니다. 단순히 X = x를 관찰하는 것은 X의 상위 변수에 관한 정보를 포함할 수 있고 이러한 변수 역시 Y에 영향을 줄 수 있기 때문에 상대적으로 약한 증거입니다.

반사실적 설명(Counterfactual Explanation)은 개별 사례(Individual Case)를 설명하는 데 특히 유용합니다. 모집단 전체의 평균 인과 효과(Average Causal Effect)만 보고하는 대신 특정 관찰 결과가 달라지기 위해 무엇이 변화했어야 하는지를 질문할 수 있습니다. 이를 통해 해당 사례에 대해 추론된 배경 조건을 유지하면서 설명을 실제 사례와 직접적으로 연결할 수 있습니다.

설명가능한 AI(Explainable AI)에서는 이러한 접근법을 이용하여 의사결정을 변경할 수 있는 최소한의 실행 가능한 변화(Minimal Feasible Change)를 식별하는 설명을 생성할 수 있습니다. 이러한 설명은 명확한 결과를 갖는 대안을 제시하기 때문에 많은 특징 중요도 점수(Feature-Importance Score)를 나열하는 것보다 이해하기 쉬운 경우가 많습니다. 그러나 제안되는 변화는 단순히 통계적으로 편리한 것이 아니라 인과적으로 타당하고 현실적이며 실행 가능(Actionable)해야 합니다.

최소성(Minimality)은 적은 수의 의미 있는 변화를 포함하는 설명이 이해하기 쉽기 때문에 중요한 특성이 될 수 있습니다. 그러나 수학적으로 가장 작은 변화가 항상 가장 좋은 인과 설명을 의미하지는 않습니다. 유용한 설명은 인과적 의존성(Causal Dependency), 시간적 순서(Temporal Ordering), 실행 가능성 제약(Feasibility Constraint), 그리고 조작 가능한 변수와 단순히 상태를 기술하는 변수의 차이도 고려해야 합니다.

인과 설명은 대조적(Contrastive)으로 구성될 수도 있습니다. 단순히 "왜 Y가 발생했는가?"라고 질문하는 대신 "왜 Y′가 아니라 Y가 발생했는가?"라고 질문할 수 있습니다. 어떤 대안적 결과와 비교하는지에 따라 관련된 인과 요인이 달라질 수 있기 때문에 설명은 이러한 대조에 의존합니다. 반사실 모델(Counterfactual Model)은 사실적 결과와 지정된 대안적 결과를 비교함으로써 이러한 형태의 추론을 자연스럽게 지원합니다.

공학 및 고장 분석(Failure Analysis)에서 인과 설명은 증상(Symptom), 기여 요인(Contributing Factor), 근본 원인(Root Cause)을 구분하는 데 도움을 줍니다. 어떤 부품이 고장과 상관되어 있더라도 두 현상이 다른 숨겨진 문제의 결과일 수 있습니다. 부품 교체, 하중 감소, 제어 로직(Control Logic) 변경과 같은 반사실적 개입을 시험함으로써 실제로 재발을 방지할 수 있는 메커니즘을 식별할 수 있습니다.

로보틱스(Robotics)에서도 실패한 행동은 인식(Perception), 계획(Planning), 제어(Control), 환경(Environment), 동역학(Dynamics)의 상호작용으로 발생하는 경우가 많기 때문에 유사한 접근법을 사용할 수 있습니다. 로봇은 다른 경로, 속도, 파지(Grasp), 상태 추정(State Estimation)을 사용했다면 결과가 달라졌을지를 분석할 수 있습니다. 이러한 설명은 디버깅(Debugging), 정책 개선(Policy Improvement), 안전한 운영, 기록된 에피소드로부터의 학습을 지원할 수 있습니다.

인과 설명은 과학적 이해가 단순한 예측 이상의 것을 요구하기 때문에 과학 AI(Scientific AI)에서도 중요합니다. 어떤 모델이 사건을 정확하게 예측하더라도 어떤 메커니즘이 그것을 발생시켰는지는 설명하지 못할 수 있습니다. 대안적 인과 구조, 개입, 반사실 결과를 비교함으로써 과학적 시스템은 경쟁 가설(Competing Hypothesis)을 평가하고 이들을 구별할 수 있는 실험을 식별할 수 있습니다.

인과 설명에서는 불확실성(Uncertainty)이 명확하게 표현되어야 합니다. 특히 중요한 변수가 잠재되어 있거나 제대로 측정되지 않은 경우 서로 다른 인과 모델이 동일한 관찰 데이터를 설명하면서 서로 다른 인과 설명을 제시할 수 있습니다. 따라서 책임 있는 설명은 하나의 이야기를 의심할 여지 없는 사실로 제시하기보다 인과 구조, 파라미터 값, 반사실 결과, 그리고 가정에 존재하는 불확실성을 반영해야 합니다.

설명의 품질은 설명을 사용하는 사용자와 목적에도 영향을 받습니다. 엔지니어는 고장이 어떻게 전파되었는지를 보여주는 메커니즘적 설명(Mechanistic Explanation)이 필요할 수 있고, 의사결정자는 실행 가능한 개입을 필요로 할 수 있으며, AI 사용자는 간결한 대조적 설명(Contrastive Explanation)을 필요로 할 수 있습니다. 동일한 인과 모델을 사용하더라도 설명 목적에 따라 서로 다른 경로, 변수, 반사실 비교를 선택할 수 있습니다.

월드 모델(World Model)은 행동과 상태가 시간에 따라 어떻게 변화하는지를 표현함으로써 인과 설명을 동적 환경(Dynamic Environment)으로 확장할 수 있습니다. 단순히 정적인 결과를 설명하는 것이 아니라 어떤 이전 행동이나 상태 전이(State Transition)가 이후의 궤적을 변화시켰는지를 식별할 수 있습니다. 이후 반사실 시뮬레이션(Counterfactual Simulation)을 통해 대안적 궤적을 재현하고 서로 다른 개입이 후속 사건을 어떻게 변화시켰을지를 분석할 수 있습니다.

자율 지능(Autonomous Intelligence)에서 인과 설명은 별도의 보고 기능이 아니라 학습 루프(Learning Loop)의 일부가 될 수 있습니다. 시스템은 결과를 관찰한 이후 관련 원인을 재구성하고, 대안적 행동을 시험하고, 반사실적 궤적을 비교하며, 내부 인과 모델(Internal Causal Model)을 업데이트할 수 있습니다. 이 경우 설명은 단순히 결과를 인간에게 전달하는 기능을 넘어 적응(Adaptation), 계획, 진단, 정책 개선에 직접적으로 기여합니다.

반사실적 추론의 전체 구조에서 인과 설명은 가정적 추론(What-if Reasoning), 반사실 모델(Counterfactual Model), 개입(Intervention), 반사실 추정(Counterfactual Estimation)을 결과가 왜 발생했는지에 대한 해석 가능한 설명으로 연결합니다. 이는 인과 계산(Causal Computation)을 메커니즘과 대안에 대한 구조화된 설명으로 변환하며, 의사결정 시스템(Decision System), AI 설명가능성(AI Explainability), 로봇 제어(Robotics Control) 응용으로 확장하기 위한 개념적 가교 역할을 합니다.

##  

## 03.06. Applications

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

Counterfactual reasoning becomes operationally valuable when it is embedded in systems that must choose actions, explain outcomes, or control physical processes. Its applications extend causal analysis from retrospective understanding toward prospective intelligence. Decision systems, explainable AI, and robotics control all benefit from comparing observed or predicted outcomes with alternatives generated under different actions, interventions, or causal conditions.

In decision systems, an intelligent agent rarely has the opportunity to execute every possible action before choosing among them. It must evaluate alternatives internally and estimate their consequences. Counterfactual reasoning provides a framework for asking what would happen under different decisions while maintaining relevant aspects of the current situation, enabling choices to be based on causal consequences rather than correlation alone.

A decision system can represent candidate actions as interventions on a causal or world model. Each intervention generates an alternative trajectory containing possible future states, rewards, costs, risks, and constraints. By comparing these trajectories, the system can select actions according to expected utility, safety, task objectives, or multiple criteria while explicitly considering how its own actions change the environment.

Counterfactual evaluation is also useful after a decision has been executed. The system can compare the observed outcome with estimated outcomes for actions that were available but not selected. This supports regret estimation, policy improvement, credit assignment, and learning from historical decisions. Valuable information can therefore be extracted from experience without physically executing every alternative policy.

Sequential decision systems require counterfactual reasoning across time rather than for isolated actions. An alternative decision at time t may change the next state, which changes later observations and available actions. The resulting counterfactual is therefore an alternative trajectory. This perspective connects causal reasoning with planning, reinforcement learning, model predictive control, and model-based decision making.

Uncertainty is essential when counterfactual estimates influence decisions. Alternative outcomes depend on incomplete observations, uncertain causal structures, stochastic dynamics, and imperfect models. A robust decision system should compare distributions over possible outcomes rather than relying only on single predictions, allowing expected benefit to be balanced against uncertainty, risk, and potentially severe failure modes.

In AI explainability, counterfactual reasoning answers a particularly intuitive question: what would need to be different for the system to produce another decision? Instead of describing a prediction only through correlations or feature importance, a counterfactual explanation identifies meaningful changes associated with a different output. This provides users with a direct contrast between the factual decision and an alternative possibility.

Useful counterfactual explanations should generally be minimal, feasible, interpretable, and causally coherent. Changing a variable independently may be misleading when that variable is constrained by other causes. An explanation should therefore respect causal dependencies and distinguish variables that can realistically be changed from variables that merely describe immutable or downstream properties of the observed situation.

Actionability is particularly important when explanations are intended to guide future behavior. A technically valid counterfactual may have little practical value if the proposed change cannot be implemented. Explainable systems should therefore search for alternatives that satisfy operational, physical, temporal, ethical, or domain-specific constraints while remaining sufficiently close to the factual case to support meaningful comparison.

Counterfactual explanations can also expose weaknesses in AI systems. If extremely small or implausible changes produce large decision shifts, the model may be unstable or relying on undesirable relationships. Comparing explanations across similar cases can reveal inconsistency, sensitivity, shortcut learning, or possible distribution problems, making counterfactual analysis useful not only for interpretation but also for model auditing.

Causal explanation strengthens this approach by distinguishing changes that merely alter a model prediction from changes that would alter the real-world outcome of interest. This distinction is critical in high-impact applications. An AI model may respond strongly to a feature that is predictive but not causally actionable, so explanation systems should avoid presenting purely statistical modifications as if they represented effective interventions.

Robotics control provides an especially direct application because robot actions are physical interventions. Commands for velocity, steering, manipulation, grasping, force, or trajectory selection deliberately modify the state of the environment. Counterfactual reasoning allows the robot to evaluate how different control actions could generate different future states before committing to an action in the physical world.

A robot approaching an obstacle, for example, may compare continuing forward, slowing, stopping, or changing direction. A manipulation robot may compare alternative grasp poses, approach directions, forces, and contact sequences. Each candidate action generates a possible future trajectory, and the controller can select the alternative that best balances task success, safety, energy consumption, stability, and execution time.

Counterfactual reasoning can operate together with a world model to provide internal action simulation. Perception estimates the current state, the world model predicts state transitions, and candidate interventions create alternative futures. The control system evaluates these futures and executes one action. New observations then provide evidence for correcting the world model, producing a continuous perception--simulation--action--learning loop.

This capability is particularly useful when physical trial and error is expensive or dangerous. Robots operating near people, industrial equipment, vehicles, hazardous environments, or valuable objects cannot safely explore every possible action. Counterfactual simulation allows many alternatives to be rejected internally, reducing unnecessary physical experimentation while preserving the ability to adapt when familiar policies become inadequate.

Recorded robot episodes provide additional opportunities for counterfactual learning. After a collision, failed grasp, localization error, unstable maneuver, or inefficient trajectory, the system can ask whether another action would have produced a better result. Reconstructing alternative trajectories helps identify whether failure originated from perception, planning, control, dynamics estimation, or environmental uncertainty.

Counterfactual analysis can consequently contribute to robot diagnosis and root-cause analysis. A failure may appear to result from an incorrect control command while actually originating from an earlier perception error or state-estimation bias. By intervening on different components of the reconstructed causal chain, the system can identify which changes would have prevented the final failure and prioritize appropriate corrective mechanisms.

For autonomous robots, counterfactual reasoning can also improve policy learning from limited data. Real-world datasets contain executed actions but not outcomes for all actions that could have been chosen. A causal world model can estimate selected alternatives and generate additional learning signals. These estimates must remain uncertainty-aware because inaccurate imagined outcomes can otherwise reinforce incorrect policies.

Decision systems, AI explainability, and robotics control therefore share a common computational pattern. The system first represents a factual state, identifies possible interventions, generates alternative outcomes or trajectories, evaluates their consequences, and compares them with the factual or predicted baseline. The result can then support action selection, explanation, diagnosis, learning, or control depending on the application.

The three application areas also reinforce one another. A robotic decision system can use counterfactual simulation to choose an action, counterfactual explanation to communicate why that action was selected, and post-action counterfactual analysis to learn from the resulting trajectory. This creates a unified architecture in which decision making, explanation, physical control, and learning operate on a shared causal representation.

The reliability of these applications ultimately depends on the quality of the causal model, state estimation, intervention definitions, and uncertainty representation. Incorrect causal assumptions can generate persuasive but invalid alternatives. Practical systems therefore require model validation, sensitivity analysis, feasibility constraints, uncertainty calibration, and continuous comparison between predicted counterfactual consequences and newly observed evidence.

Through these applications, counterfactual reasoning becomes more than a theoretical tool for asking what might have happened. It becomes a functional component of intelligent systems that evaluate unchosen decisions, explain why outcomes differ, and select physical actions by comparing possible futures. Decision systems, AI explainability, and robotics control together demonstrate how causal reasoning can support more adaptive, interpretable, and action-oriented intelligence.

반사실적 추론(Counterfactual Reasoning)은 행동을 선택하거나, 결과를 설명하거나, 물리적 프로세스를 제어해야 하는 시스템에 내장될 때 실질적인 운영 가치를 갖게 됩니다. 그 응용은 인과 분석(Causal Analysis)을 과거에 대한 회고적 이해에서 미래를 위한 전망적 지능(Prospective Intelligence)으로 확장합니다. 의사결정 시스템(Decision Systems), 설명가능한 AI(Explainable AI), 로보틱스 제어(Robotics Control)는 모두 서로 다른 행동, 개입 또는 인과 조건에서 생성된 대안을 관찰되거나 예측된 결과와 비교함으로써 이점을 얻을 수 있습니다.

의사결정 시스템에서 지능형 에이전트(Intelligent Agent)는 가능한 모든 행동을 실제로 수행해 본 후 그중 하나를 선택할 수 있는 경우가 거의 없습니다. 따라서 내부적으로 대안을 평가하고 그 결과를 추정해야 합니다. 반사실적 추론은 현재 상황의 관련 요소를 유지하면서 서로 다른 의사결정에서 어떤 일이 발생할지를 질문할 수 있는 프레임워크를 제공하며, 이를 통해 단순한 상관관계(Correlation)가 아니라 인과적 결과(Causal Consequence)를 기반으로 선택할 수 있습니다.

의사결정 시스템은 후보 행동(Candidate Action)을 인과 모델(Causal Model) 또는 월드 모델(World Model)에 대한 개입(Intervention)으로 표현할 수 있습니다. 각각의 개입은 가능한 미래 상태, 보상, 비용, 위험, 제약을 포함하는 대안적 궤적(Alternative Trajectory)을 생성합니다. 시스템은 이러한 궤적을 비교하여 기대 효용(Expected Utility), 안전성, 작업 목표 또는 여러 평가 기준에 따라 자신의 행동이 환경을 어떻게 변화시키는지를 고려하면서 행동을 선택할 수 있습니다.

반사실 평가(Counterfactual Evaluation)는 의사결정이 이미 실행된 이후에도 유용합니다. 시스템은 관찰된 결과와 선택할 수 있었지만 선택하지 않았던 행동의 추정 결과를 비교할 수 있습니다. 이는 후회 추정(Regret Estimation), 정책 개선(Policy Improvement), 신용 할당(Credit Assignment), 과거 의사결정으로부터의 학습을 지원합니다. 따라서 모든 대안적 정책을 물리적으로 실행하지 않고도 경험으로부터 가치 있는 정보를 추출할 수 있습니다.

순차적 의사결정 시스템(Sequential Decision System)은 독립된 하나의 행동이 아니라 시간에 걸친 반사실적 추론을 필요로 합니다. 시간 t에서의 대안적 의사결정은 다음 상태를 변경하고, 이는 다시 이후의 관찰과 이용 가능한 행동을 변화시킵니다. 따라서 반사실은 하나의 대안적 궤적으로 표현되며, 이러한 관점은 인과 추론을 계획(Planning), 강화학습(Reinforcement Learning), 모델 예측 제어(Model Predictive Control), 모델 기반 의사결정(Model-Based Decision Making)과 연결합니다.

반사실 추정(Counterfactual Estimation)이 의사결정에 영향을 미칠 때는 불확실성(Uncertainty)을 반드시 고려해야 합니다. 대안적 결과는 불완전한 관찰, 불확실한 인과 구조, 확률적 동역학(Stochastic Dynamics), 불완전한 모델에 의존합니다. 강건한 의사결정 시스템(Robust Decision System)은 하나의 예측값에만 의존하기보다 가능한 결과의 분포를 비교함으로써 기대 이익과 불확실성, 위험, 잠재적으로 심각한 실패 모드(Failure Mode)의 균형을 고려해야 합니다.

AI 설명가능성(AI Explainability)에서 반사실적 추론은 특히 직관적인 질문에 답합니다. 즉, 시스템이 다른 의사결정을 내리기 위해서는 무엇이 달라져야 했는지를 설명합니다. 예측을 단순히 상관관계나 특징 중요도(Feature Importance)만으로 설명하는 대신 반사실적 설명(Counterfactual Explanation)은 다른 출력과 연결되는 의미 있는 변화를 식별합니다. 이를 통해 사용자는 실제 결정과 대안적 가능성을 직접적으로 비교할 수 있습니다.

유용한 반사실적 설명은 일반적으로 최소성(Minimality), 실행 가능성(Feasibility), 해석 가능성(Interpretability), 인과적 일관성(Causal Coherence)을 갖추어야 합니다. 어떤 변수가 다른 원인에 의해 제약되는 경우 이를 독립적으로 변경하는 것은 잘못된 설명을 만들 수 있습니다. 따라서 설명은 인과적 의존성(Causal Dependency)을 존중하고 현실적으로 변경 가능한 변수와 단순히 변경할 수 없는 상태 또는 하류 속성(Downstream Property)을 기술하는 변수를 구분해야 합니다.

설명이 미래 행동을 안내하기 위한 것이라면 실행 가능성(Actionability)이 특히 중요합니다. 기술적으로 유효한 반사실이라 하더라도 제안된 변화를 실제로 구현할 수 없다면 실질적인 가치는 제한적입니다. 따라서 설명가능한 시스템은 운영적, 물리적, 시간적, 윤리적 또는 도메인 특화 제약(Domain-Specific Constraint)을 만족하면서도 의미 있는 비교가 가능하도록 실제 사례와 충분히 가까운 대안을 탐색해야 합니다.

반사실적 설명은 AI 시스템의 약점을 발견하는 데에도 활용될 수 있습니다. 매우 작거나 비현실적인 변화에 의해 의사결정이 크게 달라진다면 모델이 불안정하거나 바람직하지 않은 관계에 의존하고 있을 가능성이 있습니다. 유사한 사례들 사이의 설명을 비교하면 비일관성(Inconsistency), 민감성(Sensitivity), 지름길 학습(Shortcut Learning), 잠재적인 분포 문제(Distribution Problem)를 발견할 수 있으므로 반사실 분석은 해석뿐 아니라 모델 감사(Model Auditing)에도 유용합니다.

인과 설명(Causal Explanation)은 단순히 모델의 예측을 변경하는 변화와 실제 세계에서 관심 대상 결과를 변경하는 변화를 구분함으로써 이러한 접근법을 강화합니다. 이러한 차이는 영향력이 큰 응용 분야에서 특히 중요합니다. AI 모델은 예측에는 강하게 작용하지만 인과적으로 조작할 수 없는 특징에 민감하게 반응할 수 있으므로, 설명 시스템은 순수한 통계적 변화를 실제 효과를 갖는 개입처럼 제시해서는 안 됩니다.

로보틱스 제어(Robotics Control)는 로봇의 행동 자체가 물리적 개입(Physical Intervention)이기 때문에 반사실적 추론을 가장 직접적으로 적용할 수 있는 영역입니다. 속도, 조향, 조작, 파지(Grasping), 힘, 궤적 선택에 대한 명령은 환경의 상태를 의도적으로 변경합니다. 반사실적 추론을 이용하면 로봇은 실제 물리 세계에서 행동을 실행하기 전에 서로 다른 제어 행동이 어떤 미래 상태를 생성할지를 평가할 수 있습니다.

예를 들어 장애물에 접근하는 로봇은 계속 전진하거나, 감속하거나, 정지하거나, 방향을 변경하는 여러 대안을 비교할 수 있습니다. 조작 로봇(Manipulation Robot)은 서로 다른 파지 자세(Grasp Pose), 접근 방향, 힘, 접촉 순서를 비교할 수 있습니다. 각각의 후보 행동은 가능한 미래 궤적을 생성하며, 제어기는 작업 성공, 안전성, 에너지 소비, 안정성, 실행 시간 사이에서 가장 적절한 균형을 제공하는 대안을 선택할 수 있습니다.

반사실적 추론은 월드 모델과 결합되어 내부 행동 시뮬레이션(Internal Action Simulation)을 제공할 수 있습니다. 인식(Perception)은 현재 상태를 추정하고, 월드 모델은 상태 전이(State Transition)를 예측하며, 후보 개입은 여러 대안적 미래를 생성합니다. 제어 시스템은 이러한 미래를 평가하여 하나의 행동을 실행하고, 새로운 관찰 결과는 다시 월드 모델을 수정하는 증거로 활용됩니다. 이를 통해 지속적인 인식--시뮬레이션--행동--학습(Perception--Simulation--Action--Learning) 루프가 형성됩니다.

이러한 능력은 물리적 시행착오(Physical Trial and Error)가 비용이 많이 들거나 위험한 경우 특히 중요합니다. 사람, 산업 장비, 차량, 위험 환경 또는 고가의 물체 주변에서 작동하는 로봇은 가능한 모든 행동을 안전하게 탐색할 수 없습니다. 반사실 시뮬레이션(Counterfactual Simulation)은 많은 대안을 내부적으로 제거하여 불필요한 물리적 실험을 줄이면서 기존 정책이 적절하지 않은 상황에서도 적응할 수 있도록 합니다.

기록된 로봇 에피소드(Recorded Robot Episode)는 반사실 학습(Counterfactual Learning)을 위한 추가적인 기회를 제공합니다. 충돌, 파지 실패, 위치 추정 오류(Localization Error), 불안정한 기동 또는 비효율적인 궤적이 발생한 이후 시스템은 다른 행동이 더 나은 결과를 만들었을지를 질문할 수 있습니다. 대안적 궤적을 재구성하면 실패가 인식, 계획, 제어, 동역학 추정(Dynamics Estimation), 환경 불확실성 가운데 어디에서 시작되었는지를 식별하는 데 도움이 됩니다.

따라서 반사실 분석(Counterfactual Analysis)은 로봇 진단(Robot Diagnosis)과 근본 원인 분석(Root-Cause Analysis)에도 기여할 수 있습니다. 실패가 잘못된 제어 명령에서 발생한 것처럼 보이더라도 실제 원인은 더 이전의 인식 오류나 상태 추정 편향(State-Estimation Bias)일 수 있습니다. 재구성된 인과 사슬(Causal Chain)의 서로 다른 구성요소에 개입함으로써 어떤 변화가 최종 실패를 방지했을지를 식별하고 적절한 수정 메커니즘을 우선적으로 적용할 수 있습니다.

자율 로봇(Autonomous Robot)에서는 반사실적 추론을 이용하여 제한된 데이터로부터 정책 학습(Policy Learning)을 개선할 수도 있습니다. 실제 데이터셋에는 실행된 행동은 존재하지만 선택할 수 있었던 모든 행동의 결과는 포함되어 있지 않습니다. 인과 월드 모델(Causal World Model)은 선택된 대안들의 결과를 추정하여 추가적인 학습 신호(Learning Signal)를 생성할 수 있습니다. 그러나 부정확하게 상상된 결과가 잘못된 정책을 강화할 수 있으므로 이러한 추정에는 불확실성 인식(Uncertainty Awareness)이 반드시 필요합니다.

의사결정 시스템, AI 설명가능성, 로보틱스 제어는 공통적인 계산 패턴(Computational Pattern)을 공유합니다. 시스템은 먼저 사실적 상태(Factual State)를 표현하고, 가능한 개입을 식별하며, 대안적 결과 또는 궤적을 생성하고, 그 결과를 평가한 뒤 사실적 또는 예측 기준선(Baseline)과 비교합니다. 이후 응용 목적에 따라 이러한 결과를 행동 선택, 설명, 진단, 학습 또는 제어에 활용할 수 있습니다.

세 가지 응용 분야는 서로를 강화할 수도 있습니다. 로봇 의사결정 시스템은 행동을 선택하기 위해 반사실 시뮬레이션을 사용하고, 해당 행동이 선택된 이유를 전달하기 위해 반사실적 설명을 사용하며, 행동 이후 생성된 궤적으로부터 학습하기 위해 사후 반사실 분석(Post-Action Counterfactual Analysis)을 사용할 수 있습니다. 이를 통해 의사결정, 설명, 물리적 제어, 학습이 공유된 인과 표현(Shared Causal Representation)을 기반으로 작동하는 통합 아키텍처(Unified Architecture)를 구성할 수 있습니다.

이러한 응용의 신뢰성은 궁극적으로 인과 모델, 상태 추정(State Estimation), 개입 정의(Intervention Definition), 불확실성 표현(Uncertainty Representation)의 품질에 달려 있습니다. 잘못된 인과적 가정은 설득력 있어 보이지만 유효하지 않은 대안을 생성할 수 있습니다. 따라서 실제 시스템에서는 모델 검증(Model Validation), 민감도 분석(Sensitivity Analysis), 실행 가능성 제약, 불확실성 보정(Uncertainty Calibration), 그리고 예측된 반사실 결과와 새롭게 관찰된 증거 사이의 지속적인 비교가 필요합니다.

이러한 응용을 통해 반사실적 추론은 단순히 어떤 일이 발생할 수도 있었는지를 질문하는 이론적 도구를 넘어섭니다. 이는 선택되지 않은 의사결정을 평가하고, 결과가 왜 달라지는지를 설명하며, 가능한 미래를 비교하여 물리적 행동을 선택하는 지능형 시스템의 기능적 구성요소가 됩니다. 의사결정 시스템(Decision Systems), AI 설명가능성(AI Explainability), 로보틱스 제어(Robotics Control)는 인과 추론이 더욱 적응적이고 해석 가능하며 행동 지향적인 지능(Action-Oriented Intelligence)을 어떻게 지원할 수 있는지를 보여주는 핵심 응용 영역입니다.
