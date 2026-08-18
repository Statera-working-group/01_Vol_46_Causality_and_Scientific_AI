**Volume 46. Causality and Scientific AI**


# Chapter 06. Advanced Causality

##  

## 06.01. Causal Discovery at Scale

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal discovery at scale extends causal structure learning from relatively small datasets to systems containing thousands or millions of variables, massive observational records, heterogeneous data sources, and continuously evolving environments. The objective is to identify plausible cause--effect relationships without exhaustively testing every possible graph, while maintaining statistical reliability, computational efficiency, and meaningful representations of the underlying mechanisms.

The fundamental difficulty arises from the enormous search space of possible causal graphs. As the number of variables increases, the number of candidates directed structures grows super-exponentially, making brute-force evaluation impossible. Scalable causal discovery therefore requires algorithms that restrict candidate relationships, exploit sparsity, decompose large problems, parallelize computation, or learn continuous approximations to otherwise discrete graph-search problems.

Constraint-based methods discover causal structure by testing conditional independence relationships among variables. Algorithms derived from approaches such as PC can progressively eliminate edges that are inconsistent with observed independence patterns and orient remaining relationships when sufficient evidence exists. At large scale, their practical success depends heavily on efficient statistical tests, sparse neighborhoods, dimensionality reduction, and strategies that avoid conditioning on excessively large variable sets.

Score-based causal discovery takes a different approach by assigning candidate graphs scores representing how well they explain the data while balancing model complexity. Searching directly through all directed acyclic graphs is computationally prohibitive, so scalable methods use greedy search, local optimization, decomposable scores, heuristics, or restricted graph families. These techniques trade exhaustive guarantees for computational feasibility when the number of variables becomes large.

Continuous optimization has introduced another important direction for scalable causal discovery. Instead of treating graph edges purely as discrete decisions, adjacency structures can be represented through differentiable parameters and optimized using gradient-based learning. Acyclicity can be imposed through differentiable constraints, allowing causal graph learning to interact naturally with neural networks and modern optimization frameworks designed for high-dimensional computation.

Functional causal models provide additional information by modeling how each variable is generated from its causal parents and an independent disturbance. Assumptions about functional form, noise distributions, nonlinearities, or additive mechanisms can sometimes reveal causal direction that conditional independence alone cannot determine. At scale, neural networks and other flexible function approximators can represent complex mechanisms, although increased flexibility also raises computational and identifiability challenges.

High-dimensional data frequently contain many variables that are irrelevant to a particular causal relationship. Feature selection and dimensionality reduction therefore become essential components of scalable systems. However, ordinary compression can destroy causal information by mixing causes, effects, and confounders. Causal representation learning offers an alternative by attempting to construct lower-dimensional variables that preserve mechanisms important for causal discovery and intervention.

Large-scale discovery can also exploit modularity. Real systems are rarely fully connected; biological pathways, industrial processes, robotic systems, organizations, and physical environments often consist of interacting subsystems. A discovery pipeline can identify local neighborhoods or modules, learn causal relationships within them, and subsequently estimate connections among modules. Such decomposition reduces computational complexity while reflecting the structured organization of many real-world systems.

Temporal information provides powerful constraints when large datasets describe evolving processes. Time ordering can eliminate many impossible causal directions because future variables normally cannot cause already observed past states under standard assumptions. Time-series causal discovery can combine lagged dependencies, instantaneous relationships, state transitions, and temporal invariance to reduce the candidate graph space and reveal dynamic mechanisms operating at different time scales.

Interventional data can dramatically strengthen causal discovery because deliberate changes provide information unavailable from passive observation. Even a limited number of interventions may orient relationships that remain ambiguous in observational data. At scale, the challenge becomes experimental design: selecting interventions that maximize information about uncertain parts of a large causal graph while minimizing financial cost, operational disruption, physical risk, or experimental time.

Active causal discovery addresses this problem by allowing the learning system to choose which intervention or experiment should be performed next. Instead of collecting data uniformly, the system estimates where uncertainty in the causal structure is most consequential and selects experiments expected to reduce it. This creates an iterative cycle of graph estimation, uncertainty assessment, intervention selection, observation, and causal model refinement.

Distributed and parallel computing are increasingly important when causal discovery involves very large datasets. Conditional independence tests, local score calculations, bootstrap analyses, candidate-edge evaluations, and neural optimization can often be distributed across CPUs, GPUs, or computing nodes. Efficient implementations must minimize communication overhead and avoid repeatedly moving massive datasets, making algorithm architecture as important as statistical methodology.

Heterogeneous data introduce another scaling dimension. Modern systems may combine structured databases, images, text, sensor streams, logs, experimental measurements, and human annotations. These modalities cannot always be inserted directly into a common causal graph. Representation models can first extract meaningful variables from each modality, after which causal discovery searches for relationships among shared latent states, observed variables, actions, and contextual factors.

Foundation models and large language models can assist this process by extracting candidate causal variables and relationships from unstructured knowledge sources. Scientific papers, engineering documents, maintenance reports, or operational logs may contain valuable prior information about plausible mechanisms. Such information can constrain the search space or prioritize hypotheses, although linguistic statements should be treated as uncertain evidence rather than automatically accepted as causal truth.

Prior knowledge is particularly valuable at scale because unconstrained discovery can generate enormous numbers of candidate relationships. Physical laws, temporal ordering, known system architecture, impossible connections, expert knowledge, and previously validated mechanisms can define structural constraints. Incorporating these constraints reduces computational burden and can prevent algorithms from spending resources evaluating relationships that are physically or logically impossible.

Causal discovery at scale must also represent uncertainty rather than returning a single graph with unjustified confidence. Observational equivalence, hidden confounding, finite samples, measurement noise, and model assumptions can leave multiple structures consistent with available evidence. Confidence estimates, equivalence classes, posterior graph distributions, stability analysis, or ensembles can communicate which relationships are strongly supported and which remain uncertain.

Robustness becomes essential when datasets originate from multiple environments. A relationship appearing in one environment may reflect a temporary correlation rather than a stable mechanism. Comparing candidate structures across environments can identify relationships that persist despite distribution changes. This connects scalable causal discovery with invariant learning and causal generalization, enabling large datasets to provide environmental diversity rather than merely greater sample volume.

Robotics and Physical AI create particularly demanding large-scale causal discovery problems. A robot may simultaneously observe cameras, LiDAR, proprioception, forces, actions, objects, agents, terrain, weather, and task variables. Discovering every relationship directly is impractical. A scalable architecture must organize observations into structured states and local mechanisms, then learn how actions intervene on these mechanisms and produce changes in future states.

A causal world model can incorporate discovered mechanisms into a reusable predictive structure. Rather than maintaining one enormous undifferentiated transition model, the system can represent interacting causal modules governing motion, contact, objects, agents, sensors, and environmental dynamics. Newly discovered mechanisms can update selected modules, allowing the world model to evolve as an autonomous system accumulates experience across different environments.

Evaluation at scale requires more than comparing an estimated graph with a small known ground truth. Large systems can be evaluated through intervention prediction, edge stability, mechanism recovery, downstream decision quality, transfer across environments, computational cost, memory requirements, and scalability with increasing variables and samples. Synthetic benchmarks remain useful because exact causal structures are known, while real-world experiments test whether discovered mechanisms produce practical value.

Scalable causal discovery remains fundamentally limited by identifiability. More data and greater computational power do not automatically reveal causal direction when observational distributions are compatible with multiple causal explanations. Hidden confounders, selection effects, feedback loops, measurement errors, and latent variables further complicate discovery. Scaling must therefore include richer evidence and stronger experimental design, not merely larger algorithms.

The long-term goal of causal discovery at scale is to enable AI systems to construct and continually refine large causal models of complex environments. By combining efficient graph search, representation learning, temporal structure, interventions, prior knowledge, distributed computation, and uncertainty estimation, scalable discovery can transform massive heterogeneous datasets into structured hypotheses about how systems actually work, providing a foundation for causal world models, scientific AI, and increasingly autonomous decision-making systems.

대규모 인과 발견(Causal Discovery at Scale)은 비교적 작은 데이터셋을 대상으로 하던 인과 구조 학습(causal structure learning)을 수천 개 또는 수백만 개의 변수, 방대한 관측 기록, 이질적인 데이터 소스(heterogeneous data source), 지속적으로 변화하는 환경을 포함하는 시스템으로 확장한다. 그 목적은 가능한 모든 그래프를 완전 탐색하지 않으면서도 통계적 신뢰성(statistical reliability), 계산 효율성(computational efficiency), 그리고 기반 메커니즘에 대한 의미 있는 표현을 유지하며 타당한 원인-결과 관계(cause-effect relationship)를 식별하는 것이다.

근본적인 어려움은 가능한 인과 그래프(causal graph)의 탐색 공간(search space)이 매우 크다는 데서 발생한다. 변수의 수가 증가할수록 후보 방향성 구조(candidate directed structure)의 수는 초지수적으로(super-exponentially) 증가하기 때문에 무차별적인 완전 탐색(brute-force evaluation)은 사실상 불가능하다. 따라서 확장 가능한 인과 발견은 후보 관계를 제한하고, 희소성(sparsity)을 활용하며, 큰 문제를 분해하고, 계산을 병렬화하거나, 본래 이산적인 그래프 탐색 문제를 연속적인 근사 문제로 변환하여 학습하는 알고리즘을 필요로 한다.

제약 기반 방법(constraint-based method)은 변수들 사이의 조건부 독립성(conditional independence) 관계를 검정하여 인과 구조를 발견한다. PC와 같은 접근법에서 파생된 알고리즘은 관측된 독립성 패턴과 일치하지 않는 간선(edge)을 점진적으로 제거하고 충분한 증거가 존재할 경우 남은 관계의 방향을 결정할 수 있다. 대규모 환경에서 이러한 방법의 실용적인 성공은 효율적인 통계 검정, 희소한 이웃 구조(sparse neighborhood), 차원 축소(dimensionality reduction), 지나치게 큰 변수 집합을 조건으로 사용하는 것을 피하는 전략에 크게 의존한다.

점수 기반 인과 발견(score-based causal discovery)은 후보 그래프가 데이터를 얼마나 잘 설명하는지를 모델 복잡성과 함께 평가하는 점수(score)를 부여하는 다른 접근법을 사용한다. 모든 방향성 비순환 그래프(Directed Acyclic Graph, DAG)를 직접 탐색하는 것은 계산적으로 불가능하므로 확장 가능한 방법에서는 탐욕적 탐색(greedy search), 지역 최적화(local optimization), 분해 가능한 점수(decomposable score), 휴리스틱(heuristic), 또는 제한된 그래프 계열을 사용한다. 이러한 기법은 변수 수가 많아질 때 완전한 탐색 보장보다 계산 가능성을 우선하는 절충을 수행한다.

연속 최적화(continuous optimization)는 확장 가능한 인과 발견을 위한 또 하나의 중요한 방향을 제시했다. 그래프 간선을 순수한 이산적 결정(discrete decision)으로 취급하는 대신 인접 구조(adjacency structure)를 미분 가능한 매개변수(differentiable parameter)로 표현하고 경사 기반 학습(gradient-based learning)을 통해 최적화할 수 있다. 비순환성(acyclicity) 역시 미분 가능한 제약으로 적용할 수 있으므로 인과 그래프 학습을 신경망 및 고차원 계산을 위한 현대적인 최적화 프레임워크와 자연스럽게 결합할 수 있다.

함수적 인과 모델(functional causal model)은 각각의 변수가 자신의 인과 부모(causal parent)와 독립적인 교란항(disturbance)으로부터 어떻게 생성되는지를 모델링하여 추가적인 정보를 제공한다. 함수 형태(functional form), 잡음 분포(noise distribution), 비선형성(nonlinearity), 가법적 메커니즘(additive mechanism)에 관한 가정은 조건부 독립성만으로는 결정할 수 없는 인과 방향을 밝히는 데 도움이 될 수 있다. 대규모 시스템에서는 신경망과 기타 유연한 함수 근사기(function approximator)가 복잡한 메커니즘을 표현할 수 있지만, 유연성이 증가할수록 계산 및 식별 가능성(identifiability)의 어려움도 증가한다.

고차원 데이터(high-dimensional data)에는 특정 인과관계와 관련되지 않은 변수가 다수 포함되는 경우가 많다. 따라서 특징 선택(feature selection)과 차원 축소는 확장 가능한 시스템의 핵심 구성 요소가 된다. 그러나 일반적인 압축 방식은 원인, 결과, 교란 요인을 서로 혼합하여 인과 정보를 파괴할 수 있다. 인과 표현 학습(Causal Representation Learning)은 인과 발견과 개입에 중요한 메커니즘을 보존하는 저차원 변수를 구성함으로써 이에 대한 대안을 제공한다.

대규모 인과 발견은 모듈성(modularity)도 활용할 수 있다. 실제 시스템은 완전 연결 구조인 경우가 드물며, 생물학적 경로, 산업 공정, 로봇 시스템, 조직, 물리적 환경은 흔히 서로 상호작용하는 하위 시스템(subsystem)으로 구성된다. 인과 발견 파이프라인은 지역적인 이웃 구조나 모듈을 식별하고 각 모듈 내부의 인과관계를 학습한 후 모듈 사이의 연결을 추정할 수 있다. 이러한 분해는 계산 복잡성을 줄이면서 많은 실제 시스템의 구조적 조직 특성을 반영한다.

시간 정보(temporal information)는 대규모 데이터셋이 시간에 따라 변화하는 과정을 나타낼 때 강력한 제약 조건을 제공한다. 일반적인 가정 아래에서는 미래 변수가 이미 관측된 과거 상태의 원인이 될 수 없기 때문에 시간 순서(time ordering)를 이용하여 많은 불가능한 인과 방향을 제거할 수 있다. 시계열 인과 발견(time-series causal discovery)은 지연 의존성(lagged dependency), 순간적 관계, 상태 전이(state transition), 시간적 불변성(temporal invariance)을 결합하여 후보 그래프 공간을 줄이고 서로 다른 시간 척도에서 작동하는 동적 메커니즘을 발견할 수 있다.

개입 데이터(interventional data)는 의도적인 변화가 수동적 관측으로는 얻을 수 없는 정보를 제공하기 때문에 인과 발견을 크게 강화할 수 있다. 제한된 수의 개입만으로도 관측 데이터에서는 모호하게 남아 있는 관계의 방향을 결정할 수 있다. 대규모 환경에서 중요한 과제는 실험 설계(experimental design)이며, 이는 재정적 비용, 운영 중단, 물리적 위험, 실험 시간을 최소화하면서 거대한 인과 그래프의 불확실한 영역에 대한 정보를 최대화할 수 있는 개입을 선택하는 문제이다.

능동 인과 발견(active causal discovery)은 학습 시스템이 다음에 수행할 개입이나 실험을 직접 선택하도록 하여 이러한 문제를 다룬다. 데이터를 균일하게 수집하는 대신 시스템은 인과 구조에서 어떤 불확실성이 가장 중요한지를 추정하고 이를 가장 크게 감소시킬 것으로 예상되는 실험을 선택한다. 이를 통해 그래프 추정(graph estimation), 불확실성 평가(uncertainty assessment), 개입 선택, 관측, 인과 모델 개선(causal model refinement)이 반복되는 순환 구조를 형성한다.

분산 및 병렬 컴퓨팅(distributed and parallel computing)은 매우 큰 데이터셋에서 인과 발견을 수행할 때 점점 더 중요해지고 있다. 조건부 독립성 검정, 지역 점수 계산, 부트스트랩 분석(bootstrap analysis), 후보 간선 평가, 신경망 최적화 등은 CPU, GPU 또는 여러 컴퓨팅 노드에 분산할 수 있다. 효율적인 구현에서는 통신 오버헤드(communication overhead)를 최소화하고 방대한 데이터셋의 반복적인 이동을 방지해야 하므로 알고리즘 아키텍처 자체가 통계적 방법론만큼 중요해진다.

이질적인 데이터(heterogeneous data)는 또 다른 확장성 문제를 만든다. 현대 시스템은 구조화된 데이터베이스, 이미지, 텍스트, 센서 스트림(sensor stream), 로그(log), 실험 측정값, 인간 주석(human annotation)을 함께 사용할 수 있다. 이러한 모달리티(modality)를 항상 하나의 인과 그래프에 직접 삽입할 수 있는 것은 아니다. 먼저 표현 모델을 이용하여 각 모달리티에서 의미 있는 변수를 추출한 뒤, 공유 잠재 상태(shared latent state), 관측 변수, 행동, 맥락 요인 사이의 관계를 인과 발견 알고리즘으로 탐색할 수 있다.

파운데이션 모델(Foundation Model)과 대규모 언어 모델(Large Language Model, LLM)은 비정형 지식 소스에서 후보 인과 변수와 관계를 추출함으로써 이러한 과정을 지원할 수 있다. 과학 논문, 공학 문서, 유지보수 보고서, 운영 로그에는 타당한 메커니즘에 관한 중요한 사전 정보(prior information)가 포함될 수 있다. 이러한 정보는 탐색 공간을 제한하거나 가설의 우선순위를 결정하는 데 활용할 수 있지만, 언어로 표현된 진술을 자동으로 인과적 진실로 받아들이기보다는 불확실한 증거로 취급해야 한다.

사전 지식(prior knowledge)은 제약되지 않은 인과 발견이 엄청난 수의 후보 관계를 만들어낼 수 있기 때문에 대규모 환경에서 특히 중요하다. 물리 법칙, 시간적 순서, 알려진 시스템 아키텍처, 불가능한 연결 관계, 전문가 지식, 이미 검증된 메커니즘을 구조적 제약(structural constraint)으로 정의할 수 있다. 이러한 제약을 통합하면 계산 부담을 줄이고 물리적 또는 논리적으로 불가능한 관계를 평가하는 데 알고리즘이 자원을 낭비하는 것을 방지할 수 있다.

대규모 인과 발견은 정당화되지 않은 확신을 가진 하나의 그래프만 반환하는 대신 불확실성(uncertainty)을 표현해야 한다. 관측적 동등성(observational equivalence), 숨겨진 교란(hidden confounding), 유한한 샘플, 측정 잡음, 모델 가정으로 인해 여러 구조가 현재의 증거와 동시에 일치할 수 있다. 신뢰도 추정(confidence estimation), 동등 클래스(equivalence class), 그래프 사후 분포(posterior graph distribution), 안정성 분석(stability analysis), 앙상블(ensemble)을 통해 어떤 관계가 강하게 지지되고 어떤 관계가 여전히 불확실한지를 표현할 수 있다.

데이터셋이 여러 환경에서 수집될 경우 강건성(robustness)이 필수적이다. 하나의 환경에서 나타나는 관계는 안정적인 메커니즘이 아니라 일시적인 상관관계일 수 있다. 여러 환경에서 후보 구조를 비교하면 분포 변화에도 지속적으로 유지되는 관계를 식별할 수 있다. 이는 확장 가능한 인과 발견을 불변 학습(invariant learning) 및 인과 일반화(Causal Generalization)와 연결하며, 대규모 데이터셋의 가치를 단순한 샘플 수 증가가 아니라 환경적 다양성(environmental diversity)으로 활용할 수 있게 한다.

로보틱스(robotics)와 피지컬 인공지능(Physical AI)은 특히 까다로운 대규모 인과 발견 문제를 만든다. 로봇은 카메라, 라이다(LiDAR), 고유수용감각(proprioception), 힘(force), 행동, 객체, 에이전트, 지형, 날씨 및 작업 변수를 동시에 관측할 수 있다. 이러한 모든 관계를 직접 발견하는 것은 비현실적이다. 확장 가능한 아키텍처는 관측을 구조화된 상태와 지역 메커니즘으로 구성하고, 행동이 이러한 메커니즘에 어떻게 개입하여 미래 상태의 변화를 만들어내는지를 학습해야 한다.

인과 월드 모델(causal world model)은 발견된 메커니즘을 재사용 가능한 예측 구조로 통합할 수 있다. 하나의 거대한 비분화 전이 모델(undifferentiated transition model)을 유지하는 대신 운동, 접촉, 객체, 에이전트, 센서, 환경 동역학을 담당하는 상호작용형 인과 모듈(causal module)을 표현할 수 있다. 새롭게 발견된 메커니즘은 선택된 모듈만 갱신할 수 있으므로 자율 시스템이 서로 다른 환경에서 경험을 축적함에 따라 월드 모델도 지속적으로 발전할 수 있다.

대규모 평가(evaluation at scale)는 추정된 그래프를 작은 정답 그래프(ground truth)와 비교하는 것 이상을 요구한다. 대규모 시스템은 개입 예측(intervention prediction), 간선 안정성(edge stability), 메커니즘 복원(mechanism recovery), 후속 의사결정 품질, 환경 간 전이, 계산 비용, 메모리 요구량, 변수와 샘플 수 증가에 따른 확장성 등을 기준으로 평가할 수 있다. 합성 벤치마크(synthetic benchmark)는 정확한 인과 구조를 알고 있다는 점에서 유용하며, 실제 환경 실험은 발견된 메커니즘이 실질적인 가치를 제공하는지를 검증한다.

확장 가능한 인과 발견은 여전히 식별 가능성(identifiability)이라는 근본적인 한계를 가진다. 더 많은 데이터와 더 높은 계산 능력이 있더라도 관측 분포가 여러 인과 설명과 동시에 일치한다면 인과 방향을 자동으로 밝혀낼 수 없다. 숨겨진 교란 요인, 선택 효과(selection effect), 피드백 루프(feedback loop), 측정 오류, 잠재 변수(latent variable)는 발견을 더욱 어렵게 만든다. 따라서 확장성은 단순히 더 큰 알고리즘을 의미하는 것이 아니라 더욱 풍부한 증거와 강력한 실험 설계를 함께 포함해야 한다.

대규모 인과 발견(Causal Discovery at Scale)의 장기적인 목표는 인공지능 시스템이 복잡한 환경에 대한 대규모 인과 모델을 구축하고 지속적으로 개선하도록 만드는 것이다. 효율적인 그래프 탐색, 표현 학습, 시간적 구조, 개입, 사전 지식, 분산 컴퓨팅, 불확실성 추정을 결합함으로써 방대하고 이질적인 데이터셋을 시스템이 실제로 어떻게 작동하는지에 관한 구조화된 가설로 변환할 수 있다. 이는 인과 월드 모델(causal world model), 과학 인공지능(Scientific AI), 그리고 점점 더 자율화되는 의사결정 시스템(autonomous decision-making system)을 위한 핵심 기반을 제공한다.

##  

## 06.02. Time Series Causality [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Time-series causality studies how causal relationships unfold across ordered observations when variables influence one another through time. Unlike ordinary correlation analysis, it attempts to determine whether past changes in one process contribute to future changes in another and whether those relationships remain meaningful after accounting for alternative explanations. Time ordering provides valuable structure, but temporal precedence alone is not sufficient to establish causation.

A central principle is that causes normally precede their effects. If changes in variable X consistently occur before changes in variable Y, X becomes a plausible causal candidate for Y, whereas future values of X cannot normally explain already realized values of Y. This temporal constraint substantially reduces the space of possible causal structures, although common causes, delayed effects, feedback, and measurement timing can still create misleading dependencies.

Granger causality is one of the most widely used concepts for analyzing directional relationships in time series. Variable X is said to Granger-cause Y when past values of X improve prediction of future Y beyond the information already contained in past values of Y and other included variables. This provides an operational test of predictive direction, but Granger causality should not automatically be interpreted as proof of physical or structural causation.

Vector autoregressive models provide a classical framework for multivariate Granger analysis. Each variable is modeled using lagged values of itself and other variables, allowing researchers to test whether particular historical signals contribute additional predictive information. These models are interpretable and statistically well established, but they may struggle with nonlinear relationships, high-dimensional systems, nonstationary dynamics, and long temporal dependencies.

Transfer entropy offers an information-theoretic perspective on directional dependence. It measures whether knowledge of the past state of one process reduces uncertainty about the future state of another process beyond what can already be inferred from the target\'s own history. Because it is not restricted to linear relationships, transfer entropy can detect more complex dependencies, although reliable estimation can require substantial amounts of data.

Modern time-series causality increasingly incorporates nonlinear machine learning. Neural networks, recurrent neural networks, temporal convolutional networks, Transformers, and state-space models can represent complicated dependencies extending over multiple time scales. Causal constraints can be incorporated into these architectures so that they learn sparse directional relationships rather than merely maximizing sequence-prediction accuracy from every available signal.

Temporal causal graphs provide a structured representation of these relationships. Variables can be indexed by time, producing edges such as X at time t influencing Y at time t+1 or later. Repeated temporal structure can then be represented compactly through lagged causal relationships. Such graphs distinguish contemporaneous relationships from delayed effects and provide a foundation for reasoning about dynamic interventions and evolving system states.

Lag selection is therefore an important practical problem. A causal effect may appear immediately, after a fixed delay, or across several time scales. Choosing lags that are too short can miss important mechanisms, while excessively long lag windows increase computational complexity and introduce spurious relationships. Data-driven lag discovery, domain knowledge, multiscale modeling, and attention over historical states can help identify relevant temporal horizons.

Stationarity is another major concern because many classical methods assume that statistical relationships remain stable over time. Real systems frequently violate this assumption through aging, seasonal effects, environmental changes, policy shifts, component degradation, or changing behavior. Time-series causal analysis must therefore distinguish genuine causal changes from ordinary statistical fluctuations and identify when previously stable mechanisms have changed.

Nonstationarity can itself provide useful causal information. If different mechanisms change independently over time, shifts in distributions may help distinguish cause from effect. Comparing multiple temporal regimes can reveal which relationships remain invariant and which change together. This connects time-series causality with causal generalization, change-point detection, domain adaptation, and the broader principle of independent causal mechanisms.

Confounding remains a fundamental challenge. A third process Z may influence both X and Y at different delays, creating the appearance that X causes Y even when no direct causal relationship exists. Multivariate modeling can adjust for observed confounders, but hidden variables remain difficult. Incorporating additional sensors, latent-variable models, domain knowledge, interventions, or natural experiments can reduce ambiguity about such relationships.

Feedback loops are especially common in dynamic systems. X may influence Y, while Y subsequently influences X, creating bidirectional causal relationships across time. Control systems, biological regulation, markets, social interactions, and autonomous agents frequently exhibit such feedback. Temporal indexing makes these cycles manageable because relationships can remain acyclic across individual time steps even when the overall dynamical system contains recurrent interactions.

Interventions provide stronger evidence than passive temporal observation. If a system deliberately changes X at time t and subsequently observes a predictable change in Y, the resulting evidence can help distinguish causal effects from ordinary temporal association. Repeated interventions under different conditions are particularly valuable because they reveal whether the discovered mechanism remains stable when context and background variables change.

Counterfactual temporal reasoning asks how an observed trajectory would have evolved if an earlier event or action had been different. A causal time-series model can estimate the latent state preceding an intervention, replace the historical action or condition, and propagate the alternative dynamics forward. This capability supports planning, diagnosis, policy evaluation, fault analysis, and autonomous decision making.

Multivariate systems create significant scalability challenges because the number of possible lagged relationships increases rapidly with variables and temporal horizons. Sparse causal discovery assumes that each variable is directly influenced by only a limited subset of the available history. Regularization, graph constraints, local discovery, dimensionality reduction, and scalable optimization can therefore make causal analysis practical for large sensor networks and complex AI systems.

Multimodal temporal causality extends the problem beyond homogeneous numerical signals. Robots and intelligent systems may simultaneously process video, LiDAR, audio, language, proprioception, force measurements, and control commands. Representation learning can transform these streams into synchronized latent states, after which causal discovery can investigate how actions, objects, environmental conditions, and internal states influence one another through time.

Synchronization becomes critical in such systems. Sensors may operate at different sampling frequencies, communication delays may shift timestamps, and preprocessing pipelines may introduce additional latency. Apparent temporal order can therefore differ from true physical order. Accurate timestamping, clock synchronization, latency calibration, resampling, and uncertainty modeling are essential before causal conclusions are drawn from multimodal sequential data.

Robotics and Physical AI provide natural applications because physical behavior is fundamentally temporal. Motor commands generate forces, forces change acceleration, acceleration changes velocity, and velocity changes position. At the same time, contacts, terrain, payload, external agents, and environmental disturbances modify these transitions. Time-series causality can help separate these mechanisms and identify how actions propagate through physical state over time.

A causal world model can use these relationships to represent dynamic mechanisms rather than merely memorize trajectories. Current observations are encoded into a state, actions are represented as interventions, and causal transition mechanisms predict subsequent states. The model can then simulate alternative action sequences and reason about how different interventions propagate through the environment over multiple future time steps.

Time-series causal reasoning is also valuable for anomaly detection and predictive maintenance. Instead of detecting only that a sensor signal has become unusual, a causal model can examine which upstream mechanism may have produced the abnormal pattern and how the disturbance is propagating. This distinction can help separate root causes from downstream symptoms in industrial equipment, robots, vehicles, infrastructure, and other complex systems.

Evaluation should examine whether discovered temporal relationships support correct intervention and forecasting behavior under changing conditions. Useful criteria include causal edge recovery, lag identification, intervention-effect prediction, counterfactual trajectory accuracy, robustness to hidden confounding, and transfer across temporal regimes. Predictive accuracy alone is insufficient because a model can forecast well while relying on noncausal temporal correlations.

Time-series causality ultimately seeks to transform sequences from records of what happened into structured models of how changes propagate through time. By combining temporal ordering, lagged relationships, causal graphs, nonlinear learning, interventions, and counterfactual reasoning, it provides a foundation for understanding dynamic mechanisms and building AI systems that can predict, diagnose, plan, and intervene effectively in continuously evolving environments.

시계열 인과성(Time-Series Causality)은 변수들이 시간의 흐름에 따라 서로 영향을 미치는 순서화된 관측(ordered observation)에서 인과관계가 어떻게 전개되는지를 연구한다. 일반적인 상관관계 분석(correlation analysis)과 달리, 한 과정의 과거 변화가 다른 과정의 미래 변화에 기여하는지, 그리고 다른 가능한 설명을 고려한 이후에도 그러한 관계가 의미 있게 유지되는지를 판단하려 한다. 시간 순서는 중요한 구조를 제공하지만, 시간적 선행성(temporal precedence)만으로 인과관계를 확립할 수는 없다.

핵심 원리는 일반적으로 원인(cause)이 결과(effect)보다 먼저 발생한다는 것이다. 변수 X의 변화가 변수 Y의 변화보다 일관되게 먼저 나타난다면 X는 Y의 가능한 인과 후보(causal candidate)가 된다. 반대로 X의 미래 값은 일반적으로 이미 발생한 Y의 과거 값을 설명할 수 없다. 이러한 시간적 제약(temporal constraint)은 가능한 인과 구조의 공간을 크게 줄여주지만, 공통 원인(common cause), 지연 효과(delayed effect), 피드백(feedback), 측정 시점 등은 여전히 오해를 일으키는 의존관계를 만들 수 있다.

그레인저 인과성(Granger Causality)은 시계열의 방향성 관계(directional relationship)를 분석하는 데 가장 널리 사용되는 개념 가운데 하나이다. X의 과거 값이 Y의 과거 값과 포함된 다른 변수들이 이미 제공하는 정보를 넘어 미래의 Y를 더 잘 예측하도록 한다면 X가 Y를 그레인저 인과(Granger-cause)한다고 표현한다. 이는 예측 방향(predictive direction)에 대한 실용적인 검정을 제공하지만, 그레인저 인과성을 물리적 또는 구조적 인과관계의 증거로 자동 해석해서는 안 된다.

벡터 자기회귀 모델(Vector Autoregressive Model, VAR)은 다변량 그레인저 분석(multivariate Granger analysis)을 위한 고전적인 프레임워크를 제공한다. 각각의 변수는 자신의 과거 값과 다른 변수들의 지연 값(lagged value)을 이용하여 모델링되며, 특정 과거 신호가 추가적인 예측 정보를 제공하는지를 검정할 수 있다. 이러한 모델은 해석 가능하고 통계적으로 잘 확립되어 있지만 비선형 관계, 고차원 시스템, 비정상 동역학(nonstationary dynamics), 장기 시간 의존성을 처리하는 데 어려움을 겪을 수 있다.

전이 엔트로피(Transfer Entropy)는 방향성 의존관계를 정보이론적 관점(information-theoretic perspective)에서 분석한다. 하나의 과정에 대한 과거 상태를 알고 있을 때 대상 과정 자체의 과거만으로 추론할 수 있는 것보다 미래 상태에 대한 불확실성이 추가로 감소하는지를 측정한다. 선형 관계에 제한되지 않기 때문에 더욱 복잡한 의존성을 탐지할 수 있지만, 신뢰성 있는 추정을 위해 상당한 양의 데이터가 필요할 수 있다.

현대의 시계열 인과성은 비선형 머신러닝(nonlinear machine learning)을 점점 더 적극적으로 활용하고 있다. 신경망(neural network), 순환 신경망(Recurrent Neural Network, RNN), 시간 합성곱 신경망(Temporal Convolutional Network, TCN), 트랜스포머(Transformer), 상태 공간 모델(State-Space Model, SSM)은 여러 시간 척도에 걸친 복잡한 의존관계를 표현할 수 있다. 이러한 아키텍처에 인과 제약(causal constraint)을 적용하면 모든 가용 신호를 이용해 순차 예측 정확도만 최대화하는 대신 희소하고 방향성을 가진 관계를 학습하도록 만들 수 있다.

시간 인과 그래프(temporal causal graph)는 이러한 관계에 대한 구조화된 표현을 제공한다. 변수에 시간 인덱스(time index)를 부여하여 시간 t의 X가 시간 t+1 또는 그 이후의 Y에 영향을 주는 형태의 간선(edge)을 표현할 수 있다. 반복되는 시간 구조는 지연 인과관계(lagged causal relationship)를 이용하여 간결하게 표현할 수 있다. 이러한 그래프는 동시적 관계(contemporaneous relationship)와 지연 효과를 구별하고 동적 개입(dynamic intervention) 및 변화하는 시스템 상태에 관한 추론의 기반을 제공한다.

따라서 지연 선택(lag selection)은 중요한 실무적 문제이다. 인과 효과는 즉시 나타날 수도 있고, 일정한 시간이 지난 뒤 발생하거나, 여러 시간 척도에 걸쳐 나타날 수도 있다. 지나치게 짧은 지연을 선택하면 중요한 메커니즘을 놓칠 수 있으며, 지나치게 긴 지연 구간은 계산 복잡성을 높이고 허위 관계(spurious relationship)를 증가시킨다. 데이터 기반 지연 발견(data-driven lag discovery), 도메인 지식(domain knowledge), 다중 시간 척도 모델링(multiscale modeling), 과거 상태에 대한 어텐션(attention)을 이용하여 관련된 시간 범위를 식별할 수 있다.

정상성(stationarity)은 또 하나의 중요한 문제이다. 많은 고전적 방법은 통계적 관계가 시간에 따라 안정적으로 유지된다고 가정한다. 그러나 실제 시스템은 노화(aging), 계절적 효과(seasonal effect), 환경 변화, 정책 변화, 부품 열화(component degradation), 행동 변화 등으로 이러한 가정을 자주 위반한다. 따라서 시계열 인과 분석은 실제 인과 메커니즘의 변화와 일반적인 통계적 변동을 구별하고, 이전까지 안정적이었던 메커니즘이 언제 변화했는지를 식별해야 한다.

비정상성(nonstationarity) 자체가 유용한 인과 정보를 제공할 수도 있다. 서로 다른 메커니즘이 시간에 따라 독립적으로 변화한다면 분포의 변화는 원인과 결과를 구별하는 데 도움을 줄 수 있다. 여러 시간 구간(temporal regime)을 비교하면 어떤 관계가 불변적으로 유지되고 어떤 관계가 함께 변화하는지를 발견할 수 있다. 이는 시계열 인과성을 인과 일반화(Causal Generalization), 변화점 탐지(change-point detection), 도메인 적응(domain adaptation), 독립 인과 메커니즘(Independent Causal Mechanisms)의 원리와 연결한다.

교란(confounding)은 여전히 근본적인 문제이다. 제3의 과정 Z가 서로 다른 시간 지연을 두고 X와 Y 모두에 영향을 준다면 실제로 X와 Y 사이에 직접적인 인과관계가 없어도 X가 Y를 발생시키는 것처럼 보일 수 있다. 다변량 모델링(multivariate modeling)을 이용하면 관측된 교란 요인을 조정할 수 있지만 숨겨진 변수(hidden variable)는 여전히 어렵다. 추가 센서, 잠재 변수 모델(latent-variable model), 도메인 지식, 개입 또는 자연 실험(natural experiment)을 활용하면 이러한 관계의 모호성을 줄일 수 있다.

피드백 루프(feedback loop)는 동적 시스템에서 특히 흔하게 나타난다. X가 Y에 영향을 주고 이후 Y가 다시 X에 영향을 주면서 시간에 걸쳐 양방향 인과관계(bidirectional causal relationship)를 형성할 수 있다. 제어 시스템, 생물학적 조절, 시장, 사회적 상호작용, 자율 에이전트에서 이러한 피드백이 흔하게 나타난다. 시간 인덱싱(temporal indexing)을 이용하면 전체 동적 시스템에 순환적 상호작용이 존재하더라도 개별 시간 단계 사이의 관계를 비순환 구조로 표현할 수 있다.

개입(intervention)은 수동적인 시간 관측보다 더욱 강력한 증거를 제공한다. 시스템이 시간 t에서 X를 의도적으로 변경하고 이후 Y에서 예측 가능한 변화가 발생하는 것을 관측한다면, 이러한 증거는 실제 인과 효과와 단순한 시간적 연관성을 구별하는 데 도움을 줄 수 있다. 서로 다른 조건에서 반복적으로 수행된 개입은 맥락과 배경 변수가 달라져도 발견된 메커니즘이 안정적으로 유지되는지를 보여주기 때문에 특히 중요하다.

반사실적 시간 추론(counterfactual temporal reasoning)은 이전의 사건이나 행동이 달랐다면 관측된 궤적(observed trajectory)이 어떻게 전개되었을지를 질문한다. 인과 시계열 모델은 개입 이전의 잠재 상태(latent state)를 추정하고 과거의 행동이나 조건을 다른 것으로 대체한 뒤 대안적인 동역학을 미래로 전개할 수 있다. 이러한 능력은 계획(planning), 진단(diagnosis), 정책 평가(policy evaluation), 고장 분석(fault analysis), 자율 의사결정(autonomous decision making)을 지원한다.

다변량 시스템(multivariate system)은 변수와 시간 범위가 증가함에 따라 가능한 지연 관계의 수가 빠르게 증가하기 때문에 상당한 확장성 문제를 발생시킨다. 희소 인과 발견(sparse causal discovery)은 각각의 변수가 사용 가능한 과거 정보 가운데 제한된 일부에 의해서만 직접적인 영향을 받는다고 가정한다. 정규화(regularization), 그래프 제약(graph constraint), 지역적 인과 발견, 차원 축소 및 확장 가능한 최적화를 이용하면 대규모 센서 네트워크와 복잡한 인공지능 시스템에서도 인과 분석을 실용적으로 수행할 수 있다.

다중 모달 시간 인과성(multimodal temporal causality)은 문제를 동일한 종류의 수치 신호를 넘어 확장한다. 로봇과 지능형 시스템은 비디오, 라이다(LiDAR), 오디오, 언어, 고유수용감각(proprioception), 힘 측정(force measurement), 제어 명령(control command)을 동시에 처리할 수 있다. 표현 학습(representation learning)을 이용하여 이러한 스트림을 동기화된 잠재 상태(synchronized latent state)로 변환한 후 행동, 객체, 환경 조건 및 내부 상태가 시간에 따라 서로 어떻게 영향을 주는지를 인과 발견을 통해 분석할 수 있다.

이러한 시스템에서는 동기화(synchronization)가 매우 중요해진다. 센서마다 서로 다른 샘플링 주파수(sampling frequency)로 동작할 수 있고, 통신 지연(communication delay)이 타임스탬프(timestamp)를 이동시키며, 전처리 파이프라인이 추가적인 지연(latency)을 발생시킬 수 있다. 따라서 관측된 시간적 순서가 실제 물리적 순서와 다를 수 있다. 다중 모달 순차 데이터에서 인과적 결론을 도출하기 전에 정확한 타임스탬프, 클록 동기화(clock synchronization), 지연 보정(latency calibration), 리샘플링(resampling), 불확실성 모델링(uncertainty modeling)이 필요하다.

로보틱스(robotics)와 피지컬 인공지능(Physical AI)은 물리적 행동 자체가 본질적으로 시간적 과정이기 때문에 자연스러운 응용 분야를 제공한다. 모터 명령(motor command)은 힘을 발생시키고, 힘은 가속도를 변화시키며, 가속도는 속도를 변화시키고, 속도는 위치를 변화시킨다. 동시에 접촉, 지형, 페이로드(payload), 외부 에이전트, 환경 교란(environmental disturbance)이 이러한 전이에 영향을 준다. 시계열 인과성은 이러한 메커니즘을 분리하고 행동의 영향이 시간에 따라 물리적 상태로 어떻게 전파되는지를 식별하는 데 도움을 줄 수 있다.

인과 월드 모델(causal world model)은 이러한 관계를 활용하여 단순히 궤적을 암기하는 대신 동적 메커니즘(dynamic mechanism)을 표현할 수 있다. 현재 관측은 상태(state)로 부호화되고 행동은 개입으로 표현되며, 인과 전이 메커니즘(causal transition mechanism)은 이후의 상태를 예측한다. 모델은 여러 대안적인 행동 시퀀스를 시뮬레이션하고 서로 다른 개입이 여러 미래 시간 단계에 걸쳐 환경에 어떻게 전파되는지를 추론할 수 있다.

시계열 인과 추론(time-series causal reasoning)은 이상 탐지(anomaly detection)와 예지 정비(predictive maintenance)에서도 유용하다. 단순히 센서 신호가 비정상적으로 변했다는 사실만 탐지하는 것이 아니라, 어떤 상위 메커니즘(upstream mechanism)이 비정상적인 패턴을 발생시켰으며 그 교란이 어떻게 전파되고 있는지를 분석할 수 있다. 이러한 구분은 산업 장비, 로봇, 차량, 인프라 및 기타 복잡한 시스템에서 근본 원인(root cause)과 후속 증상(downstream symptom)을 분리하는 데 도움을 준다.

평가(evaluation)는 발견된 시간적 관계가 변화하는 조건에서도 올바른 개입 및 예측 행동을 지원하는지를 검증해야 한다. 유용한 평가 기준에는 인과 간선 복원(causal edge recovery), 지연 식별(lag identification), 개입 효과 예측(intervention-effect prediction), 반사실적 궤적 정확도(counterfactual trajectory accuracy), 숨겨진 교란에 대한 강건성(robustness), 서로 다른 시간 구간 사이의 전이 능력이 포함된다. 모델은 비인과적 시간 상관관계에 의존하면서도 높은 예측 성능을 보일 수 있기 때문에 예측 정확도만으로는 충분하지 않다.

궁극적으로 시계열 인과성(Time-Series Causality)은 순차 데이터를 단순히 무엇이 발생했는지를 기록한 데이터에서 변화가 시간에 따라 어떻게 전파되는지를 설명하는 구조화된 모델(structured model)로 변환하는 것을 목표로 한다. 시간적 순서, 지연 관계, 인과 그래프, 비선형 학습, 개입 및 반사실적 추론을 결합함으로써 동적 메커니즘을 이해하고, 지속적으로 변화하는 환경에서 효과적으로 예측하고 진단하며 계획하고 개입할 수 있는 인공지능 시스템을 구축하기 위한 기반을 제공한다.

##  

## 06.03. Multimodal Causality

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Multimodal causality studies causal relationships when information about a system is distributed across multiple forms of observation such as images, video, language, audio, LiDAR, force measurements, proprioception, physiological signals, and structured data. Instead of analyzing each modality independently, it seeks shared causal mechanisms that explain how events observed through different sensory channels arise, interact, and influence future outcomes.

The central challenge is that different modalities provide distinct but overlapping views of the same underlying world. A camera may reveal object appearance and motion, LiDAR may describe geometry and distance, audio may indicate contact or mechanical events, and language may provide semantic context. Multimodal causal reasoning attempts to identify latent variables that generate these observations while separating genuine causes from modality-specific correlations and measurement artifacts.

A useful conceptual framework assumes that an underlying causal state produces observations through different measurement processes. The physical state of an object, for example, may simultaneously determine its visual appearance, spatial geometry, acoustic response, and tactile properties. Rather than treating these signals as unrelated features, a causal model represents them as consequences of shared latent causes and uses their agreement or disagreement to refine its understanding of the environment.

Multimodal representation learning therefore plays an important role. Encoders transform heterogeneous inputs into latent representations that can be aligned, fused, or organized into structured variables. Ordinary multimodal learning may optimize similarity or prediction across modalities, whereas causal representation learning attempts to preserve factors corresponding to stable mechanisms. The objective is to discover representations that remain meaningful when sensors, environments, or observational conditions change.

Cross-modal relationships can provide evidence that is unavailable within a single modality. If visual motion is consistently followed by a contact force and a characteristic sound, the combination can provide stronger evidence about an interaction than any individual signal. However, repeated co-occurrence alone does not establish causality. Temporal ordering, interventions, structural assumptions, and contextual variation are still required to distinguish common causes from direct causal influence.

Synchronization is particularly important because causal interpretation depends on the order in which events occur. Cameras, microphones, LiDARs, inertial sensors, and control systems frequently operate at different sampling frequencies and latencies. Incorrect timestamps can reverse apparent temporal relationships or create false delays. Multimodal causal systems therefore require accurate time alignment, latency calibration, resampling, and explicit modeling of synchronization uncertainty.

Missing modalities create another practical challenge. Sensors may fail, become occluded, lose communication, or operate unreliably under particular environmental conditions. A robust causal model should not depend on every modality being continuously available. If different observations are connected through shared causal variables, the system can use available modalities to infer missing information while representing increased uncertainty rather than simply assuming that absent measurements are normal.

Confounding can occur both within and across modalities. Environmental lighting may influence several cameras, terrain may affect both vibration and wheel slip, and human activity may simultaneously change audio and visual observations. Without modeling such common causes, a system may incorrectly conclude that one sensor signal causes another. Multimodal causal discovery therefore requires reasoning about shared confounders, sensor-specific noise, latent variables, and measurement mechanisms.

Interventions provide especially valuable information in multimodal systems. When an agent performs an action, the consequences may appear simultaneously across several sensory channels. A robot pushing an object may observe visual displacement, force variation, motor current changes, and contact sounds. Because the action is deliberately selected, these synchronized responses provide evidence about how an intervention propagates through physical mechanisms and becomes observable through different modalities.

Counterfactual reasoning can then operate across modalities. After observing an event, a model can estimate what visual, acoustic, geometric, or force-related observations might have occurred if an earlier action had been different. Such reasoning requires a shared causal state rather than independent predictors for every sensor. The alternative causal state is propagated through modality-specific observation models to generate consistent counterfactual consequences across sensory channels.

Causal graphs provide a structured representation for these relationships. Nodes can represent latent physical states, semantic concepts, actions, environmental conditions, and modality-specific observations. Directed edges describe how causes propagate from hidden mechanisms toward observable signals. Separating world-state variables from measurement variables is particularly useful because sensor readings should often be modeled as effects of physical conditions rather than as direct causes of those conditions.

Attention and Transformer architectures can support multimodal causal modeling by selecting relationships among tokens originating from different sensory streams. Cross-attention can associate language with visual objects, actions with observed motion, or force events with contact regions. Yet attention weights alone do not establish causal influence. Causal constraints and intervention-based evidence are needed to determine whether an attended relationship corresponds to an actual mechanism.

Multimodal foundation models create opportunities for learning causal knowledge from very large heterogeneous datasets. Models trained jointly on text, images, video, sensor streams, and actions can acquire broad representations of objects, events, and interactions. Causal structure can organize these representations around mechanisms rather than purely statistical alignment, potentially improving transfer when a system encounters new combinations of environments, sensors, objects, or tasks.

Language has a distinctive role because it can provide semantic descriptions of relationships that are difficult to infer from raw sensor data alone. Instructions, maintenance reports, scientific documents, and human explanations may describe possible causes, failures, constraints, or expected effects. These descriptions can supply prior hypotheses for causal discovery, while physical observations and interventions provide evidence for testing whether the linguistic hypotheses correspond to actual mechanisms.

Temporal modeling is essential because multimodal causal processes evolve through time. Video frames, control commands, force signals, and language events can be represented as synchronized sequences of latent states. Temporal causal models can identify immediate and delayed effects while separating persistent state from transient observations. This enables reasoning about how actions propagate through physical dynamics and subsequently appear in multiple sensing channels.

Multimodal causal discovery must also address dimensionality. Raw images and point clouds may contain millions of measurements, making direct causal graph discovery impractical. Hierarchical representations can first organize data into objects, surfaces, agents, contacts, events, and other meaningful entities. Causal discovery can then operate on these structured variables rather than individual pixels or points, greatly reducing the search space while improving interpretability.

Robotics and Physical AI provide a natural setting for this approach. An embodied robot continuously integrates vision, LiDAR, inertial measurements, proprioception, force sensing, localization, language instructions, and control commands. These signals describe different aspects of a single physical process. Multimodal causality can connect them through shared mechanisms, allowing the robot to distinguish what it observes from what its own actions cause.

For example, wheel slip may be reflected simultaneously in commanded velocity, encoder measurements, inertial motion, visual odometry, and terrain appearance. A purely correlational model may associate any one of these signals with failure. A causal multimodal model can instead represent terrain properties and traction as underlying mechanisms that influence several measurements, helping the robot diagnose the cause and select an appropriate corrective action.

Manipulation provides another example. Object geometry can be observed visually or through depth sensing, contact can be detected through force and tactile signals, and action is represented by joint commands and end-effector motion. Combining these modalities causally allows a robot to reason about how grasp configuration and applied force produce object motion, rather than merely learning statistical associations between sensor patterns and successful manipulation.

Autonomous vehicles similarly depend on multimodal causal understanding. Cameras, radar, LiDAR, maps, vehicle dynamics, driver or planner commands, and communication systems provide complementary information. A causal representation can separate environmental state from sensor measurement and distinguish external events from changes caused by the vehicle\'s own actions. This supports more reliable prediction when individual sensors become uncertain or environmental conditions change.

Causal world models can integrate these ideas into a unified architecture. Multimodal observations are encoded into a structured latent world state, actions are represented as interventions, causal dynamics predict future states, and modality-specific decoders predict future observations. Planning can operate primarily in the causal state space while sensory predictions provide consistency checks against what the system expects to observe after executing an action.

Evaluation should therefore measure more than multimodal prediction accuracy. Important criteria include recovery of shared causal variables, intervention-effect prediction, robustness when modalities are missing or corrupted, counterfactual consistency across sensors, transfer to new environments, and performance under sensor distribution shifts. A system should preserve causal conclusions even when superficial properties of individual modalities change.

Significant limitations remain because multimodal data do not automatically resolve causal ambiguity. Multiple sensors may simply provide several correlated measurements of the same uncertain process, while hidden confounders can influence all modalities simultaneously. Sensor bias, synchronization errors, representation mistakes, and incomplete interventions can produce convincing but incorrect causal structures. Multimodal diversity must therefore be combined with appropriate assumptions and experimental evidence.

Ultimately, multimodal causality seeks to transform heterogeneous sensory information into a coherent model of how the underlying world works. By combining representation learning, temporal alignment, causal graphs, interventions, counterfactual reasoning, and structured world models, it enables AI systems to connect what they see, hear, measure, read, and do through shared mechanisms. This capability is especially important for robust Physical AI operating in complex, changing, and partially observable environments.

다중 모달 인과성(Multimodal Causality)은 시스템에 관한 정보가 이미지, 비디오, 언어, 오디오, 라이다(LiDAR), 힘 측정(force measurement), 고유수용감각(proprioception), 생리적 신호(physiological signal), 구조화 데이터(structured data) 등 여러 형태의 관측에 분산되어 있을 때의 인과관계를 연구한다. 각각의 모달리티(modality)를 독립적으로 분석하는 대신, 서로 다른 감각 채널에서 관측되는 사건이 어떻게 발생하고 상호작용하며 미래 결과에 영향을 미치는지를 설명하는 공유 인과 메커니즘(shared causal mechanism)을 찾는 것을 목표로 한다.

핵심적인 과제는 서로 다른 모달리티가 동일한 기반 세계(underlying world)에 대해 서로 다르면서도 중첩되는 관점을 제공한다는 점이다. 카메라는 객체의 외형과 운동을 보여주고, 라이다는 기하 구조와 거리를 설명하며, 오디오는 접촉이나 기계적 사건을 나타내고, 언어는 의미적 맥락(semantic context)을 제공할 수 있다. 다중 모달 인과 추론(multimodal causal reasoning)은 이러한 관측을 생성하는 잠재 변수(latent variable)를 식별하면서 실제 원인을 모달리티별 상관관계 및 측정 인공물(measurement artifact)과 분리하려 한다.

유용한 개념적 프레임워크에서는 기반 인과 상태(underlying causal state)가 서로 다른 측정 과정을 통해 관측을 생성한다고 가정한다. 예를 들어 객체의 물리적 상태(physical state)는 시각적 외형, 공간 기하 구조, 음향 반응, 촉각적 특성을 동시에 결정할 수 있다. 인과 모델(causal model)은 이러한 신호를 서로 관련 없는 특징으로 취급하는 대신 공유 잠재 원인(shared latent cause)의 결과로 표현하고, 모달리티 사이의 일치 또는 불일치를 이용하여 환경에 대한 이해를 개선한다.

따라서 다중 모달 표현 학습(multimodal representation learning)은 중요한 역할을 한다. 인코더(encoder)는 이질적인 입력을 정렬, 융합 또는 구조화된 변수로 구성할 수 있는 잠재 표현(latent representation)으로 변환한다. 일반적인 다중 모달 학습은 모달리티 사이의 유사성이나 예측을 최적화할 수 있지만, 인과 표현 학습(causal representation learning)은 안정적인 메커니즘에 대응하는 요인을 보존하려 한다. 목표는 센서, 환경 또는 관측 조건이 변화하더라도 의미를 유지하는 표현을 발견하는 것이다.

교차 모달 관계(cross-modal relationship)는 단일 모달리티만으로는 얻을 수 없는 증거를 제공할 수 있다. 시각적 움직임 이후 접촉력이 발생하고 특징적인 소리가 일관되게 나타난다면, 이러한 조합은 개별 신호보다 상호작용에 대한 더 강력한 증거를 제공할 수 있다. 그러나 반복적인 동시 발생만으로 인과성을 확립할 수는 없다. 공통 원인(common cause)과 직접적인 인과 영향을 구별하려면 시간적 순서, 개입(intervention), 구조적 가정(structural assumption), 맥락 변화가 여전히 필요하다.

인과적 해석은 사건이 발생하는 순서에 의존하기 때문에 동기화(synchronization)가 특히 중요하다. 카메라, 마이크, 라이다, 관성 센서(inertial sensor), 제어 시스템은 서로 다른 샘플링 주파수와 지연 시간(latency)으로 동작하는 경우가 많다. 잘못된 타임스탬프(timestamp)는 겉으로 보이는 시간적 관계를 역전시키거나 거짓 지연(false delay)을 만들 수 있다. 따라서 다중 모달 인과 시스템에는 정확한 시간 정렬(time alignment), 지연 보정(latency calibration), 리샘플링(resampling), 동기화 불확실성에 대한 명시적인 모델링이 필요하다.

누락된 모달리티(missing modality)는 또 다른 실질적인 과제를 만든다. 센서는 고장 나거나, 가려지거나, 통신이 끊기거나, 특정 환경 조건에서 신뢰성이 떨어질 수 있다. 강건한 인과 모델(robust causal model)은 모든 모달리티가 지속적으로 사용 가능하다는 가정에 의존해서는 안 된다. 서로 다른 관측이 공유 인과 변수를 통해 연결되어 있다면 사용 가능한 모달리티를 이용하여 누락된 정보를 추론하면서, 없는 측정을 정상 상태라고 단순히 가정하는 대신 증가된 불확실성을 표현할 수 있다.

교란(confounding)은 개별 모달리티 내부뿐 아니라 모달리티 사이에서도 발생할 수 있다. 환경 조명은 여러 카메라에 동시에 영향을 미칠 수 있고, 지형은 진동과 휠 슬립(wheel slip)에 모두 영향을 줄 수 있으며, 인간 활동은 오디오와 시각 관측을 동시에 변화시킬 수 있다. 이러한 공통 원인을 모델링하지 않으면 하나의 센서 신호가 다른 센서 신호의 원인이라고 잘못 판단할 수 있다. 따라서 다중 모달 인과 발견(multimodal causal discovery)은 공유 교란 요인(shared confounder), 센서별 잡음, 잠재 변수, 측정 메커니즘에 관한 추론을 필요로 한다.

개입(intervention)은 다중 모달 시스템에서 특히 가치 있는 정보를 제공한다. 에이전트(agent)가 행동을 수행하면 그 결과가 여러 감각 채널에서 동시에 나타날 수 있다. 로봇이 객체를 밀면 시각적 변위(visual displacement), 힘의 변화, 모터 전류 변화, 접촉음을 함께 관측할 수 있다. 행동이 의도적으로 선택되었기 때문에 이러한 동기화된 반응은 개입의 영향이 물리적 메커니즘을 통해 어떻게 전파되고 서로 다른 모달리티를 통해 관측되는지를 보여주는 증거를 제공한다.

이후 반사실적 추론(counterfactual reasoning)을 여러 모달리티에 걸쳐 수행할 수 있다. 사건을 관측한 후 모델은 이전 행동이 달랐다면 시각적, 음향적, 기하학적 또는 힘과 관련된 관측이 어떻게 달라졌을지를 추정할 수 있다. 이러한 추론에는 각 센서를 위한 독립적인 예측기가 아니라 공유 인과 상태(shared causal state)가 필요하다. 대안적인 인과 상태를 모달리티별 관측 모델(modality-specific observation model)을 통해 전파하여 감각 채널 전반에서 일관된 반사실적 결과를 생성할 수 있다.

인과 그래프(causal graph)는 이러한 관계를 구조적으로 표현하는 방법을 제공한다. 노드(node)는 잠재 물리 상태(latent physical state), 의미적 개념(semantic concept), 행동, 환경 조건 및 모달리티별 관측을 나타낼 수 있다. 방향성 간선(directed edge)은 숨겨진 메커니즘에서 관측 가능한 신호로 원인의 영향이 어떻게 전파되는지를 표현한다. 특히 세계 상태 변수(world-state variable)와 측정 변수(measurement variable)를 분리하면 센서 측정값을 물리적 조건의 직접적인 원인이 아니라 그 결과로 모델링할 수 있다는 점에서 유용하다.

어텐션(attention)과 트랜스포머(Transformer) 아키텍처는 서로 다른 감각 스트림에서 생성된 토큰 사이의 관계를 선택함으로써 다중 모달 인과 모델링을 지원할 수 있다. 교차 어텐션(cross-attention)은 언어와 시각 객체, 행동과 관측된 운동, 힘 이벤트와 접촉 영역을 연결할 수 있다. 그러나 어텐션 가중치(attention weight) 자체가 인과 영향을 확립하는 것은 아니다. 어텐션된 관계가 실제 메커니즘에 대응하는지를 결정하려면 인과 제약(causal constraint)과 개입 기반 증거가 필요하다.

다중 모달 파운데이션 모델(multimodal foundation model)은 매우 큰 이질적 데이터셋에서 인과 지식을 학습할 수 있는 가능성을 제공한다. 텍스트, 이미지, 비디오, 센서 스트림, 행동을 공동으로 학습한 모델은 객체, 사건 및 상호작용에 대한 광범위한 표현을 획득할 수 있다. 인과 구조는 이러한 표현을 단순한 통계적 정렬(statistical alignment)이 아니라 메커니즘을 중심으로 구성하여 새로운 환경, 센서, 객체 또는 작업의 조합을 만났을 때 전이 성능을 향상시킬 가능성이 있다.

언어(language)는 원시 센서 데이터만으로 추론하기 어려운 관계에 대한 의미적 설명을 제공할 수 있다는 점에서 독특한 역할을 한다. 지시문(instruction), 유지보수 보고서, 과학 문서, 인간의 설명에는 가능한 원인, 고장, 제약 조건 또는 예상 결과가 기술될 수 있다. 이러한 설명은 인과 발견을 위한 사전 가설(prior hypothesis)을 제공할 수 있으며, 물리적 관측과 개입은 언어적 가설이 실제 메커니즘과 대응하는지를 검증하기 위한 증거를 제공한다.

다중 모달 인과 과정은 시간에 따라 전개되므로 시간 모델링(temporal modeling)이 필수적이다. 비디오 프레임, 제어 명령, 힘 신호, 언어 이벤트를 동기화된 잠재 상태의 시퀀스로 표현할 수 있다. 시간 인과 모델(temporal causal model)은 지속적인 상태와 일시적인 관측을 분리하면서 즉각적인 효과와 지연된 효과를 식별할 수 있다. 이를 통해 행동이 물리적 동역학을 통해 전파되고 이후 여러 감각 채널에 어떻게 나타나는지를 추론할 수 있다.

다중 모달 인과 발견은 차원성(dimensionality) 문제도 해결해야 한다. 원시 이미지와 포인트 클라우드(point cloud)는 수백만 개의 측정값을 포함할 수 있기 때문에 직접적인 인과 그래프 발견은 현실적으로 어렵다. 계층적 표현(hierarchical representation)을 이용하여 데이터를 먼저 객체, 표면, 에이전트, 접촉, 사건 및 기타 의미 있는 개체로 구성할 수 있다. 이후 개별 픽셀이나 포인트가 아니라 이러한 구조화된 변수를 대상으로 인과 발견을 수행하면 탐색 공간을 크게 줄이고 해석 가능성(interpretability)을 향상시킬 수 있다.

로보틱스(robotics)와 피지컬 인공지능(Physical AI)은 이러한 접근법을 적용하기에 자연스러운 환경을 제공한다. 체화된 로봇(embodied robot)은 비전, 라이다, 관성 측정, 고유수용감각, 힘 센싱(force sensing), 위치 추정(localization), 언어 지시, 제어 명령을 지속적으로 통합한다. 이러한 신호는 하나의 물리적 과정에 대한 서로 다른 측면을 설명한다. 다중 모달 인과성은 공유 메커니즘을 통해 이들을 연결하여 로봇이 자신이 단순히 관측한 변화와 자신의 행동으로 발생시킨 변화를 구별하도록 할 수 있다.

예를 들어 휠 슬립(wheel slip)은 명령 속도(commanded velocity), 엔코더 측정값(encoder measurement), 관성 운동, 시각 오도메트리(visual odometry), 지형의 외형에 동시에 반영될 수 있다. 순수한 상관관계 모델은 이러한 신호 가운데 하나를 고장과 연결할 수 있다. 반면 다중 모달 인과 모델은 지형 특성(terrain property)과 접지력(traction)을 여러 측정값에 영향을 주는 기반 메커니즘으로 표현하여 로봇이 원인을 진단하고 적절한 보정 행동(corrective action)을 선택하도록 지원할 수 있다.

조작(manipulation)은 또 다른 사례를 제공한다. 객체의 기하 구조(object geometry)는 비전이나 깊이 센싱(depth sensing)을 통해 관측할 수 있고, 접촉은 힘과 촉각 신호(tactile signal)를 통해 탐지할 수 있으며, 행동은 관절 명령(joint command)과 말단장치 운동(end-effector motion)으로 표현된다. 이러한 모달리티를 인과적으로 결합하면 로봇은 단순히 센서 패턴과 성공적인 조작 사이의 통계적 연관성을 학습하는 대신 파지 구성(grasp configuration)과 적용된 힘이 객체 운동을 어떻게 발생시키는지를 추론할 수 있다.

자율주행차(autonomous vehicle) 역시 다중 모달 인과 이해에 의존한다. 카메라, 레이더(radar), 라이다, 지도, 차량 동역학(vehicle dynamics), 운전자 또는 플래너 명령(planner command), 통신 시스템은 상호 보완적인 정보를 제공한다. 인과 표현은 환경 상태와 센서 측정을 분리하고 외부 사건과 차량 자체의 행동으로 발생한 변화를 구별할 수 있다. 이를 통해 개별 센서의 불확실성이 증가하거나 환경 조건이 변화하더라도 더욱 신뢰성 있는 예측을 지원할 수 있다.

인과 월드 모델(causal world model)은 이러한 개념들을 하나의 통합된 아키텍처로 결합할 수 있다. 다중 모달 관측은 구조화된 잠재 세계 상태(structured latent world state)로 부호화되고, 행동은 개입으로 표현되며, 인과 동역학(causal dynamics)은 미래 상태를 예측한다. 이후 모달리티별 디코더(modality-specific decoder)가 미래 관측을 예측한다. 계획(planning)은 주로 인과 상태 공간에서 수행되고, 감각 예측은 행동 실행 이후 시스템이 예상한 관측과 실제 관측이 일치하는지를 확인하는 일관성 검증(consistency check)을 제공한다.

따라서 평가는 단순한 다중 모달 예측 정확도(multimodal prediction accuracy) 이상을 측정해야 한다. 중요한 기준에는 공유 인과 변수(shared causal variable)의 복원, 개입 효과 예측(intervention-effect prediction), 모달리티가 누락되거나 손상되었을 때의 강건성(robustness), 센서 사이의 반사실적 일관성(counterfactual consistency), 새로운 환경으로의 전이, 센서 분포 변화(sensor distribution shift)에서의 성능이 포함된다. 개별 모달리티의 표면적 특성이 변화하더라도 시스템은 인과적 결론을 유지할 수 있어야 한다.

다중 모달 데이터가 자동으로 인과적 모호성(causal ambiguity)을 해결하는 것은 아니기 때문에 여전히 중요한 한계가 존재한다. 여러 센서는 동일한 불확실한 과정에 대해 서로 상관된 여러 측정값을 제공할 뿐일 수 있으며, 숨겨진 교란 요인(hidden confounder)은 모든 모달리티에 동시에 영향을 줄 수도 있다. 센서 편향(sensor bias), 동기화 오류, 표현 오류, 불완전한 개입은 그럴듯하지만 잘못된 인과 구조를 만들어낼 수 있다. 따라서 다중 모달 다양성은 적절한 가정과 실험적 증거(experimental evidence)와 결합되어야 한다.

궁극적으로 다중 모달 인과성(Multimodal Causality)은 이질적인 감각 정보를 기반 세계가 실제로 어떻게 작동하는지를 설명하는 일관된 모델로 변환하는 것을 목표로 한다. 표현 학습, 시간 정렬, 인과 그래프, 개입, 반사실적 추론, 구조화된 월드 모델(structured world model)을 결합함으로써 인공지능 시스템이 보고, 듣고, 측정하고, 읽고, 행동하는 모든 정보를 공유 메커니즘을 통해 연결하도록 한다. 이러한 능력은 복잡하고 변화하며 부분적으로 관측 가능한 환경에서 동작해야 하는 강건한 피지컬 인공지능(robust Physical AI)에 특히 중요하다.

##  

## 06.04. Causal World Models

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal world models extend predictive world modeling by representing not only how environments are likely to evolve, but also why state transitions occur and how actions or interventions alter future outcomes. A conventional world model may learn statistical regularities between observations, actions, and future states. A causal world model instead attempts to organize these relationships around stable mechanisms that describe how changes propagate through the environment.

The central distinction lies between prediction and intervention. Predictive models estimate what is likely to happen given the current state and historical behavior, whereas causal models ask what would happen if an agent deliberately changed some part of the system. Actions are therefore represented as interventions on the world state, allowing the model to distinguish naturally occurring transitions from changes produced directly by the agent.

A causal world model typically transforms high-dimensional observations into a structured latent state. Images, LiDAR, audio, proprioception, force measurements, language, and other sensory signals may be compressed into variables describing objects, agents, positions, velocities, contacts, materials, goals, and environmental conditions. These variables provide a more suitable foundation for causal reasoning than raw pixels or unstructured sensor measurements.

Structural causal models provide a conceptual framework for organizing these latent variables. Each state variable can be generated by causal parents, external disturbances, and structural mechanisms. Directed relationships describe how changes in one variable influence others. When extended through time, this structure forms a dynamic causal model capable of representing how actions and environmental processes jointly determine future states.

Causal transition models are therefore more structured than ordinary learned dynamics. Instead of approximating the entire transition from one latent vector to another with a single undifferentiated function, the model can represent separate mechanisms for motion, contact, object interaction, agent behavior, sensing, and environmental dynamics. Such modularity makes it possible to identify which mechanism is responsible when predictions fail.

The principle of independent causal mechanisms is particularly important. Different parts of the world may operate according to mechanisms that are relatively autonomous even though their outputs interact. A change in terrain friction should not require relearning how a camera projects geometry, and a new object appearance should not necessarily alter the mechanics of collision. Modular causal models seek to preserve these separations.

Temporal causality provides the dynamic foundation of a causal world model. Current states influence future states through mechanisms operating over different time scales. Some effects are immediate, such as contact force after collision, while others develop gradually, such as acceleration changing velocity and position. Modeling temporal direction and lag enables the system to distinguish causes from downstream consequences within evolving trajectories.

Multimodal causality strengthens the model because the same physical state is often observed through several sensors. Object motion may simultaneously change camera images, LiDAR geometry, inertial measurements, and proprioceptive signals. A causal world model can treat these measurements as consequences of a shared underlying state rather than independent features, improving consistency when individual sensors become noisy, unavailable, or unreliable.

Actions provide particularly valuable causal information because embodied agents actively intervene in their environments. A robot can accelerate, steer, push, grasp, rotate, or release objects and observe the resulting state changes. Repeated interaction allows the world model to learn action-effect relationships that passive observation alone may not reveal, gradually transforming experience into a structured model of environmental dynamics.

Intervention modeling enables planning beyond trajectory imitation. Given a current causal state, the system can apply hypothetical actions internally and propagate their consequences through learned mechanisms. Several candidate interventions can therefore be evaluated before physical execution. This supports model-based control in situations where real-world experimentation is expensive, slow, energy-intensive, or potentially dangerous.

Counterfactual reasoning extends internal simulation by asking how an already observed trajectory would have changed under an alternative action. The model estimates the relevant background state, replaces one intervention, and propagates the modified dynamics forward. Such reasoning can support failure analysis, policy improvement, diagnosis, explanation, and learning from previous decisions without repeating every experience physically.

Object-centric representations are especially useful because physical interactions often occur among persistent entities. Instead of representing a scene as one global latent vector, the model can maintain states for objects, agents, surfaces, and environmental components. Relations among these entities describe contact, proximity, support, visibility, ownership, or interaction, enabling causal mechanisms to operate on reusable entities rather than fixed scene configurations.

Graph-based architectures naturally support this representation. Nodes can encode entities and latent state variables, while directed or relational edges describe possible interactions. Graph neural networks can approximate mechanisms through message passing, while causal constraints restrict which relationships should be interpreted as influence. Dynamic graphs can change as objects enter, leave, contact, or separate from one another.

Uncertainty must also be represented explicitly because a world model never has complete information. Partial observability, sensor noise, hidden variables, uncertain object properties, and unpredictable external agents can produce several plausible future states. A causal world model should therefore represent distributions over latent states, mechanisms, or trajectories rather than treating one predicted future as certain.

Causal discovery can allow the world model to evolve instead of relying entirely on a predefined structure. As the agent accumulates observations and interventions, it can search for previously unknown dependencies among states and actions. Newly discovered mechanisms can be incorporated into the model, while relationships that repeatedly fail under intervention or environmental change can be revised or assigned lower confidence.

Causal generalization becomes possible when the model separates stable mechanisms from environment-specific correlations. A robot trained in one location may encounter different lighting, textures, objects, payloads, or terrain elsewhere. If the underlying mechanics remain similar, the model can reuse relevant causal modules while adapting only those mechanisms that actually changed, reducing the amount of new experience required.

Compositional generalization follows from the same modular structure. Familiar objects, actions, and mechanisms may appear in combinations never observed during training. A model that has independently learned grasping, rigid-body motion, collision, and support relationships can potentially combine these mechanisms in a new scene. This is more flexible than memorizing complete trajectories or scene-specific statistical patterns.

Hierarchical causal world models can represent mechanisms at multiple levels of abstraction. Low-level variables may describe forces, joint states, velocity, and contact, while higher levels represent objects, actions, goals, tasks, and semantic events. Causal relationships across these levels connect physical dynamics with planning concepts, allowing an autonomous system to reason from motor commands to task-level consequences.

Language can provide another abstraction layer. Instructions such as "move the container without blocking the doorway" describe goals and constraints rather than direct motor commands. A language model can translate these semantic requirements into candidate changes in the causal world state, while the world model evaluates whether proposed action sequences produce the required physical consequences without violating constraints.

Reinforcement learning can use causal world models to improve exploration and policy learning. Instead of discovering useful actions entirely through trial and error, an agent can plan using its internal model and direct real-world exploration toward uncertain mechanisms. Experience becomes valuable not only for obtaining reward but also for reducing uncertainty about causal relationships that influence future decisions.

Safety is a major motivation for this approach. Autonomous systems must often evaluate consequences that should not be tested directly. A robot should not need to experience every collision, unstable grasp, or dangerous trajectory before learning to avoid it. Causal simulation can estimate how hazardous states arise and allow planners to reject interventions that propagate toward unsafe outcomes.

For Physical AI, the causal world model can become the central bridge between perception, reasoning, planning, and control. Multimodal observations estimate the current world state, causal dynamics predict how that state can change, planning evaluates interventions, and control executes selected actions. New observations then update the internal state, producing a continuous perception--prediction--intervention--observation loop.

Evaluation must extend beyond next-state prediction accuracy. A causal world model should be tested on intervention-effect prediction, counterfactual consistency, mechanism identification, transfer across environments, adaptation after dynamics changes, multimodal robustness, and planning performance. A model that predicts familiar trajectories accurately may still fail when asked to reason about actions or situations outside its training distribution.

Important limitations remain because causal structure cannot generally be identified from passive observations alone. Hidden confounders, incomplete interventions, partial observability, incorrect representations, and changing mechanisms can all produce misleading models. Reliable causal world modeling therefore requires interaction, environmental diversity, temporal information, suitable inductive biases, prior knowledge, and explicit uncertainty management.

Ultimately, causal world models aim to transform learned environmental prediction into mechanism-aware internal simulation. By combining structured representations, temporal and multimodal causality, interventions, counterfactual reasoning, causal discovery, and modular dynamics, they provide a foundation for AI systems that can understand how actions change the world, imagine alternative futures, generalize beyond familiar conditions, and plan safely in complex physical environments.

인과 월드 모델(Causal World Models)은 환경이 앞으로 어떻게 변화할 가능성이 있는지를 표현하는 것뿐만 아니라, 상태 전이(state transition)가 왜 발생하는지 그리고 행동이나 개입(intervention)이 미래 결과를 어떻게 변화시키는지를 표현함으로써 예측 월드 모델링(predictive world modeling)을 확장한다. 일반적인 월드 모델(world model)은 관측, 행동, 미래 상태 사이의 통계적 규칙성을 학습할 수 있지만, 인과 월드 모델은 변화가 환경을 통해 어떻게 전파되는지를 설명하는 안정적인 메커니즘(stable mechanism)을 중심으로 이러한 관계를 구성하려 한다.

핵심적인 차이는 예측(prediction)과 개입(intervention) 사이에 있다. 예측 모델은 현재 상태와 과거 행동이 주어졌을 때 무엇이 발생할 가능성이 높은지를 추정하지만, 인과 모델은 에이전트(agent)가 시스템의 일부를 의도적으로 변화시켰을 때 무엇이 발생할지를 질문한다. 따라서 행동(action)은 세계 상태(world state)에 대한 개입으로 표현되며, 이를 통해 모델은 자연적으로 발생하는 전이와 에이전트가 직접 만들어낸 변화를 구별할 수 있다.

인과 월드 모델은 일반적으로 고차원 관측(high-dimensional observation)을 구조화된 잠재 상태(structured latent state)로 변환한다. 이미지, 라이다(LiDAR), 오디오, 고유수용감각(proprioception), 힘 측정(force measurement), 언어 및 기타 감각 신호는 객체, 에이전트, 위치, 속도, 접촉, 재질, 목표 및 환경 조건을 설명하는 변수로 압축될 수 있다. 이러한 변수는 원시 픽셀이나 구조화되지 않은 센서 측정값보다 인과 추론(causal reasoning)에 더욱 적합한 기반을 제공한다.

구조적 인과 모델(Structural Causal Model, SCM)은 이러한 잠재 변수를 구성하기 위한 개념적 프레임워크를 제공한다. 각각의 상태 변수는 인과 부모(causal parent), 외부 교란(external disturbance), 구조적 메커니즘(structural mechanism)에 의해 생성될 수 있다. 방향성 관계(directed relationship)는 하나의 변수 변화가 다른 변수에 어떻게 영향을 미치는지를 나타낸다. 이러한 구조를 시간 방향으로 확장하면 행동과 환경 과정이 미래 상태를 어떻게 공동으로 결정하는지를 표현하는 동적 인과 모델(dynamic causal model)이 된다.

따라서 인과 전이 모델(causal transition model)은 일반적인 학습 동역학(learned dynamics)보다 더욱 구조화되어 있다. 하나의 잠재 벡터에서 다른 잠재 벡터로의 전체 전이를 하나의 비분화된 함수(undifferentiated function)로 근사하는 대신, 운동, 접촉, 객체 상호작용, 에이전트 행동, 센싱(sensing), 환경 동역학을 담당하는 개별 메커니즘을 표현할 수 있다. 이러한 모듈성(modularity)을 통해 예측이 실패했을 때 어떤 메커니즘이 원인인지를 식별할 수 있다.

독립 인과 메커니즘(Independent Causal Mechanisms)의 원리는 특히 중요하다. 세계의 서로 다른 부분은 그 출력이 상호작용하더라도 비교적 독립적인 메커니즘에 따라 작동할 수 있다. 지형의 마찰(friction)이 변화했다고 해서 카메라가 기하 구조를 투영하는 방식을 다시 학습할 필요는 없으며, 새로운 객체의 외형이 충돌 역학(collision mechanics)을 반드시 변화시키는 것도 아니다. 모듈형 인과 모델(modular causal model)은 이러한 분리를 유지하는 것을 목표로 한다.

시간 인과성(temporal causality)은 인과 월드 모델의 동적 기반을 제공한다. 현재 상태는 서로 다른 시간 척도에서 작동하는 메커니즘을 통해 미래 상태에 영향을 준다. 충돌 직후 발생하는 접촉력처럼 일부 효과는 즉각적으로 나타나지만, 가속도가 속도와 위치를 변화시키는 것처럼 다른 효과는 점진적으로 전개된다. 시간 방향과 지연(lag)을 모델링하면 변화하는 궤적 안에서 원인과 그 이후에 발생하는 결과를 구별할 수 있다.

다중 모달 인과성(multimodal causality)은 동일한 물리적 상태가 여러 센서를 통해 관측되는 경우가 많기 때문에 모델을 더욱 강화한다. 객체의 움직임은 카메라 이미지, 라이다 기하 구조, 관성 측정값, 고유수용감각 신호를 동시에 변화시킬 수 있다. 인과 월드 모델은 이러한 측정값을 서로 독립적인 특징으로 취급하는 대신 공유된 기반 상태(shared underlying state)의 결과로 처리할 수 있으며, 개별 센서에 잡음이 발생하거나 사용할 수 없거나 신뢰성이 저하되었을 때에도 일관성을 향상시킬 수 있다.

행동(action)은 체화된 에이전트(embodied agent)가 환경에 능동적으로 개입하기 때문에 특히 가치 있는 인과 정보를 제공한다. 로봇은 가속하고, 조향하고, 밀고, 잡고, 회전시키거나 객체를 놓은 후 그에 따른 상태 변화를 관측할 수 있다. 반복적인 상호작용을 통해 월드 모델은 수동적인 관측만으로는 발견하기 어려운 행동-결과 관계(action-effect relationship)를 학습하며, 경험을 점진적으로 환경 동역학에 대한 구조화된 모델로 변환할 수 있다.

개입 모델링(intervention modeling)은 단순한 궤적 모방(trajectory imitation)을 넘어서는 계획(planning)을 가능하게 한다. 현재 인과 상태가 주어지면 시스템은 가상의 행동을 내부적으로 적용하고 학습된 메커니즘을 통해 그 결과를 전파할 수 있다. 따라서 실제 환경에서 행동을 실행하기 전에 여러 후보 개입을 평가할 수 있다. 이는 실제 실험에 높은 비용이나 시간이 필요하거나 많은 에너지를 소비하고 잠재적인 위험까지 존재하는 상황에서 모델 기반 제어(model-based control)를 지원한다.

반사실적 추론(counterfactual reasoning)은 이미 관측된 궤적에서 다른 행동이 수행되었다면 어떻게 달라졌을지를 질문함으로써 내부 시뮬레이션(internal simulation)을 확장한다. 모델은 관련된 배경 상태를 추정하고 하나의 개입을 다른 것으로 대체한 다음 수정된 동역학을 미래로 전개한다. 이러한 추론은 모든 경험을 물리적으로 반복하지 않고도 고장 분석(failure analysis), 정책 개선(policy improvement), 진단, 설명 및 이전 의사결정으로부터의 학습을 지원할 수 있다.

객체 중심 표현(object-centric representation)은 물리적 상호작용이 지속적으로 존재하는 개체(entity) 사이에서 발생하는 경우가 많기 때문에 특히 유용하다. 장면 전체를 하나의 전역 잠재 벡터(global latent vector)로 표현하는 대신 객체, 에이전트, 표면 및 환경 구성 요소별 상태를 유지할 수 있다. 이러한 개체 사이의 관계는 접촉, 근접성, 지지(support), 가시성(visibility), 소유 또는 상호작용을 표현하며, 인과 메커니즘이 고정된 장면 구성 대신 재사용 가능한 개체를 대상으로 작동하도록 한다.

그래프 기반 아키텍처(graph-based architecture)는 이러한 표현을 자연스럽게 지원한다. 노드(node)는 개체와 잠재 상태 변수를 부호화하고, 방향성 또는 관계형 간선(relational edge)은 가능한 상호작용을 표현할 수 있다. 그래프 신경망(Graph Neural Network, GNN)은 메시지 전달(message passing)을 통해 메커니즘을 근사할 수 있으며, 인과 제약(causal constraint)은 어떤 관계를 실제 영향으로 해석해야 하는지를 제한한다. 동적 그래프(dynamic graph)는 객체가 등장하거나 사라지고, 접촉하거나 분리됨에 따라 변화할 수 있다.

월드 모델은 완전한 정보를 가질 수 없기 때문에 불확실성(uncertainty) 역시 명시적으로 표현되어야 한다. 부분 관측 가능성(partial observability), 센서 잡음, 숨겨진 변수(hidden variable), 불확실한 객체 특성, 예측하기 어려운 외부 에이전트로 인해 여러 개의 가능한 미래 상태가 존재할 수 있다. 따라서 인과 월드 모델은 하나의 예측된 미래를 확정적인 것으로 취급하기보다 잠재 상태, 메커니즘 또는 궤적에 대한 확률 분포(distribution)를 표현해야 한다.

인과 발견(causal discovery)을 이용하면 월드 모델이 완전히 사전 정의된 구조에만 의존하지 않고 지속적으로 발전할 수 있다. 에이전트가 관측과 개입 경험을 축적하면서 상태와 행동 사이에서 이전에 알려지지 않았던 의존관계를 탐색할 수 있다. 새롭게 발견된 메커니즘은 모델에 통합할 수 있으며, 개입이나 환경 변화에서 반복적으로 실패하는 관계는 수정하거나 신뢰도(confidence)를 낮출 수 있다.

모델이 안정적인 메커니즘과 환경에 특화된 상관관계를 분리하면 인과 일반화(causal generalization)가 가능해진다. 하나의 장소에서 훈련된 로봇이 다른 장소에서 서로 다른 조명, 질감, 객체, 페이로드(payload), 지형을 만날 수 있다. 기반 역학이 유사하게 유지된다면 모델은 관련된 인과 모듈(causal module)을 재사용하고 실제로 변화한 메커니즘만 적응시킬 수 있으므로 새로운 경험에 필요한 데이터의 양을 줄일 수 있다.

조합적 일반화(compositional generalization) 역시 동일한 모듈 구조에서 발생한다. 익숙한 객체, 행동 및 메커니즘이 훈련 과정에서는 경험하지 못했던 새로운 조합으로 등장할 수 있다. 파지(grasping), 강체 운동(rigid-body motion), 충돌, 지지 관계를 독립적으로 학습한 모델은 이러한 메커니즘을 새로운 장면에서 결합할 가능성이 있다. 이는 완전한 궤적이나 장면에 특화된 통계 패턴을 암기하는 것보다 더욱 유연하다.

계층적 인과 월드 모델(hierarchical causal world model)은 여러 추상화 수준(abstraction level)에서 메커니즘을 표현할 수 있다. 저수준 변수는 힘, 관절 상태, 속도, 접촉 등을 나타내고, 상위 수준에서는 객체, 행동, 목표, 작업 및 의미적 사건(semantic event)을 표현할 수 있다. 이러한 수준 사이의 인과관계는 물리적 동역학과 계획 개념을 연결하여 자율 시스템이 모터 명령(motor command)에서 작업 수준 결과(task-level consequence)까지 추론하도록 한다.

언어(language)는 또 다른 추상화 계층을 제공할 수 있다. "출입구를 막지 않으면서 컨테이너를 이동하라"와 같은 지시는 직접적인 모터 명령이 아니라 목표와 제약 조건을 설명한다. 언어 모델(language model)은 이러한 의미적 요구사항을 인과 세계 상태에서의 후보 변화로 변환할 수 있으며, 월드 모델은 제안된 행동 시퀀스가 제약을 위반하지 않으면서 필요한 물리적 결과를 만들어내는지를 평가할 수 있다.

강화학습(reinforcement learning)은 인과 월드 모델을 활용하여 탐색(exploration)과 정책 학습(policy learning)을 향상시킬 수 있다. 에이전트는 유용한 행동을 전적으로 시행착오(trial and error)를 통해 발견하는 대신 내부 모델을 이용해 계획하고, 불확실한 메커니즘을 중심으로 실제 환경 탐색을 수행할 수 있다. 경험은 보상을 획득하는 데뿐만 아니라 미래 의사결정에 영향을 미치는 인과관계의 불확실성을 줄이는 데에도 중요한 가치를 갖게 된다.

안전성(safety)은 이러한 접근법의 중요한 동기이다. 자율 시스템은 직접 시험해서는 안 되는 결과까지 평가해야 하는 경우가 많다. 로봇은 모든 충돌, 불안정한 파지, 위험한 궤적을 직접 경험한 이후에야 이를 피하도록 학습해서는 안 된다. 인과 시뮬레이션(causal simulation)은 위험 상태가 어떻게 발생하는지를 추정하고, 플래너(planner)가 위험한 결과로 전파될 가능성이 있는 개입을 거부하도록 할 수 있다.

피지컬 인공지능(Physical AI)에서 인과 월드 모델은 지각(perception), 추론(reasoning), 계획(planning), 제어(control)를 연결하는 핵심적인 다리가 될 수 있다. 다중 모달 관측은 현재 세계 상태를 추정하고, 인과 동역학은 그 상태가 어떻게 변화할 수 있는지를 예측하며, 계획은 가능한 개입을 평가하고, 제어는 선택된 행동을 실행한다. 이후 새로운 관측이 내부 상태를 갱신하면서 지속적인 지각-예측-개입-관측(perception--prediction--intervention--observation) 순환 구조를 형성한다.

평가(evaluation)는 단순한 다음 상태 예측(next-state prediction)의 정확도를 넘어 확장되어야 한다. 인과 월드 모델은 개입 효과 예측(intervention-effect prediction), 반사실적 일관성(counterfactual consistency), 메커니즘 식별(mechanism identification), 환경 간 전이, 동역학 변화 이후의 적응, 다중 모달 강건성(multimodal robustness), 계획 성능 등을 기준으로 평가해야 한다. 익숙한 궤적을 정확하게 예측하는 모델이라도 훈련 분포 밖의 행동이나 상황에 대해 추론하도록 요구받으면 실패할 수 있다.

인과 구조는 일반적으로 수동적인 관측만으로 완전히 식별할 수 없기 때문에 중요한 한계가 남아 있다. 숨겨진 교란 요인(hidden confounder), 불완전한 개입, 부분 관측 가능성, 잘못된 표현, 변화하는 메커니즘은 모두 잘못된 모델을 만들어낼 수 있다. 따라서 신뢰성 있는 인과 월드 모델링(causal world modeling)을 위해서는 상호작용, 환경 다양성(environmental diversity), 시간 정보, 적절한 귀납적 편향(inductive bias), 사전 지식(prior knowledge), 명시적인 불확실성 관리가 필요하다.

궁극적으로 인과 월드 모델(Causal World Models)은 학습된 환경 예측을 메커니즘 인식 내부 시뮬레이션(mechanism-aware internal simulation)으로 전환하는 것을 목표로 한다. 구조화된 표현, 시간 및 다중 모달 인과성, 개입, 반사실적 추론, 인과 발견, 모듈형 동역학(modular dynamics)을 결합함으로써 행동이 세계를 어떻게 변화시키는지를 이해하고, 대안적인 미래를 상상하며, 익숙하지 않은 조건으로 일반화하고, 복잡한 물리적 환경에서 안전하게 계획할 수 있는 인공지능 시스템의 기반을 제공한다.

##  

## 06.05. AGI and Causality

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Artificial General Intelligence requires more than the ability to recognize patterns and generate plausible responses across many tasks. A generally intelligent system must understand how changes in the world produce consequences, distinguish correlation from causation, and determine which actions can deliberately alter future states. Causality therefore provides a possible foundation for moving from statistical competence toward flexible reasoning, intervention, and autonomous adaptation.

Modern AI systems learn remarkably rich statistical structures from large datasets, but statistical association alone can fail when familiar correlations disappear. An AGI operating across changing environments cannot assume that relationships observed during training will always remain valid. It must identify mechanisms that remain stable across contexts and separate them from temporary correlations created by particular datasets, environments, cultures, sensors, or historical conditions.

Causal representation is important because intelligence operates on meaningful factors rather than raw observations alone. Images, language, sensor streams, actions, and memories must be transformed into internal variables representing objects, agents, goals, physical states, intentions, constraints, and environmental conditions. If these representations correspond to causal factors, an AGI can reason about how changing one part of a situation may influence other parts.

Intervention provides a deeper level of reasoning than observation. An intelligent agent should not only estimate what is likely to happen next, but also ask what would happen if it performed a particular action. Actions can be represented as interventions that modify selected variables or mechanisms within an internal world model. This allows an AGI to evaluate possible consequences before committing to actions in the external environment.

Counterfactual reasoning further enables an AGI to learn from possibilities that were never directly experienced. After observing an outcome, the system can ask how events might have unfolded if another decision had been made or a different condition had existed. Such reasoning supports explanation, error analysis, responsibility assessment, strategy improvement, and learning from previous experience without physically repeating every alternative action.

A causal world model can provide the internal structure needed for these capabilities. Rather than predicting future observations as an undifferentiated sequence, the model represents entities, states, actions, relationships, and transition mechanisms. An AGI can use this model to simulate interventions, compare alternative futures, identify mechanisms responsible for outcomes, and update selected components when its expectations disagree with new observations.

Temporal causality is essential because intelligent behavior unfolds through sequences of events. Actions influence states, states influence later opportunities, and delayed consequences may appear long after the original decision. An AGI must distinguish immediate effects from downstream consequences and understand feedback loops operating across multiple time scales. This enables planning beyond short-term correlations and supports reasoning about long-horizon objectives.

Multimodal causality is equally important because a generally intelligent system may receive information through language, vision, audio, touch, proprioception, structured databases, and other channels. These observations should not be treated as independent descriptions of reality. They often arise from shared underlying causes. Integrating them through common causal states can produce a more coherent and robust understanding of the environment.

Causal discovery allows an AGI to extend its knowledge beyond mechanisms supplied during training. When the system encounters unfamiliar environments, it can observe relationships, perform safe interventions, compare alternative hypotheses, and revise its internal causal structure. Intelligence then becomes an iterative process of forming hypotheses, gathering evidence, testing mechanisms, and updating beliefs rather than merely applying a fixed pretrained model.

Active learning naturally follows from this perspective. An AGI does not need to collect information passively or explore randomly. It can identify which uncertainty matters for its current goals and select observations or interventions expected to provide the most informative evidence. This transforms exploration into purposeful experimentation and can substantially reduce the experience required to understand unfamiliar systems.

Causal generalization is central to transferring knowledge across environments. If an AGI learns that a mechanism remains stable while superficial properties change, it can reuse that mechanism in new contexts. Changes in appearance, language, location, sensor configuration, or task description should not require complete relearning when the underlying causal structure remains similar. This supports robust out-of-distribution behavior.

Modularity strengthens this form of generalization. Complex environments can be represented as collections of interacting causal mechanisms rather than one monolithic predictive function. When one mechanism changes, an AGI can revise that component while preserving unaffected knowledge. Such modularity supports efficient adaptation, continual learning, and compositional reasoning by allowing previously learned mechanisms to be recombined in unfamiliar situations.

Compositional reasoning is particularly important for general intelligence because new problems frequently consist of familiar elements arranged in unfamiliar combinations. An AGI may understand individual objects, actions, physical principles, and social constraints without having encountered their exact combination before. Causal representations allow these components to be recombined according to their mechanisms rather than requiring memorized examples for every possible situation.

Hierarchical causality can connect different levels of abstraction. Low-level mechanisms may describe forces, motion, signals, or neural computations, while higher levels represent objects, goals, plans, organizations, and social interactions. An AGI must reason across these levels without assuming that every useful explanation exists at the same resolution. Different tasks require different causal abstractions while remaining connected to underlying mechanisms.

Language can provide a powerful interface to causal knowledge. Human explanations frequently describe reasons, consequences, intentions, conditions, and hypothetical alternatives. Large language models can extract and manipulate this knowledge, but linguistic plausibility alone does not establish causal truth. An AGI must connect language-based hypotheses with observations, external knowledge, experiments, tools, and world models to determine which explanations are supported.

Memory also interacts closely with causal reasoning. Episodic memory can preserve particular experiences, while semantic memory can store generalized mechanisms extracted from many events. An AGI can compare new situations with previous episodes, identify which causal structures remain relevant, and revise mechanisms when repeated evidence contradicts them. Memory therefore becomes more than retrieval; it contributes to continuous causal model construction.

Planning can be understood as causal reasoning over possible futures. Given goals and constraints, an AGI can generate candidate actions, intervene on its internal world model, simulate resulting state transitions, and compare expected outcomes. Planning becomes especially powerful when the model can represent uncertainty and alternative causal hypotheses, allowing the agent to choose actions that both accomplish goals and reduce important uncertainty.

Causal reasoning can also support safety. A generally capable autonomous system may encounter situations that were not anticipated by its designers, making fixed rules insufficient. Understanding how actions propagate toward hazards allows the system to reject plans that create unsafe downstream states. Counterfactual simulation can further evaluate dangerous possibilities internally rather than requiring harmful outcomes to be experienced directly.

Social intelligence introduces additional causal complexity because other agents possess goals, beliefs, knowledge, and intentions that influence their behavior. An AGI interacting with humans must distinguish observable behavior from the hidden factors that may generate it while maintaining uncertainty about those factors. Causal models of agents can support cooperation and communication, but they must avoid treating uncertain inferred intentions as established facts.

Scientific reasoning represents another important connection between AGI and causality. Science advances by proposing explanations, deriving predictions, designing experiments, performing interventions, and revising theories. An AGI capable of participating in this cycle would need to compare competing causal models rather than simply summarize existing information. Causal reasoning therefore connects general intelligence with autonomous hypothesis formation and discovery.

Embodied AGI makes causality especially concrete because physical actions generate direct intervention data. A robot can manipulate objects, move through environments, observe consequences, and refine its understanding of physical mechanisms. Perception estimates the current state, the world model predicts consequences, planning evaluates interventions, control executes actions, and new observations provide evidence for updating the internal causal model.

Uncertainty must remain explicit throughout this process. Causal relationships are rarely known with complete certainty, particularly in partially observable or unfamiliar environments. An AGI should maintain alternative hypotheses, estimate confidence, seek additional evidence when necessary, and avoid converting weak correlations into confident causal conclusions. Calibrated uncertainty is therefore as important as the ability to construct causal explanations.

Evaluating causal capabilities in AGI requires tests beyond conventional benchmark accuracy. Systems should be evaluated on intervention reasoning, counterfactual consistency, causal discovery, mechanism transfer, compositional generalization, adaptation after environmental change, long-horizon planning, and robustness to altered correlations. Strong performance on familiar tasks does not demonstrate general causal intelligence if the system fails when underlying conditions change.

Major theoretical limitations remain because causality cannot always be recovered from observational data. Different causal structures may generate identical statistical patterns, and hidden confounders can make apparently reasonable explanations incorrect. AGI therefore cannot obtain reliable causal knowledge from scale alone. Interaction, interventions, temporal evidence, prior knowledge, experimental design, and explicit assumptions remain necessary for resolving many causal ambiguities.

AGI and causality ultimately converge on the problem of building systems that can understand, predict, and intentionally influence a changing world. Causal representations transform observations into mechanisms, interventions connect reasoning with action, counterfactuals support alternative futures, and causal discovery enables continuous learning. Together, these capabilities provide a pathway from pattern-based intelligence toward adaptive agents that can reason about why events occur and how their actions can change what happens next.

인공 일반 지능(Artificial General Intelligence, AGI)은 단순히 여러 작업에서 패턴을 인식하고 그럴듯한 응답을 생성하는 능력 이상을 필요로 한다. 일반 지능 시스템(generally intelligent system)은 세계의 변화가 어떻게 결과를 만들어내는지 이해하고, 상관관계(correlation)와 인과관계(causation)를 구별하며, 어떤 행동이 미래 상태를 의도적으로 변화시킬 수 있는지를 판단해야 한다. 따라서 인과성(causality)은 통계적 능력에서 유연한 추론, 개입(intervention), 자율적 적응(autonomous adaptation)으로 발전하기 위한 하나의 기반을 제공할 수 있다.

현대 인공지능 시스템은 대규모 데이터셋으로부터 매우 풍부한 통계적 구조(statistical structure)를 학습하지만, 익숙한 상관관계가 사라질 경우 통계적 연관성만으로는 실패할 수 있다. 변화하는 환경에서 동작하는 AGI는 훈련 과정에서 관측된 관계가 항상 유효할 것이라고 가정할 수 없다. 특정 데이터셋, 환경, 문화, 센서 또는 역사적 조건에 의해 만들어진 일시적인 상관관계와 다양한 맥락에서도 안정적으로 유지되는 메커니즘을 구별해야 한다.

인과 표현(causal representation)은 지능이 원시 관측(raw observation)만이 아니라 의미 있는 요인에 기반하여 작동하기 때문에 중요하다. 이미지, 언어, 센서 스트림(sensor stream), 행동 및 기억은 객체, 에이전트(agent), 목표, 물리적 상태, 의도, 제약 조건, 환경 조건을 나타내는 내부 변수로 변환되어야 한다. 이러한 표현이 인과 요인(causal factor)에 대응한다면 AGI는 상황의 한 부분을 변화시켰을 때 다른 부분이 어떻게 영향을 받을지를 추론할 수 있다.

개입(intervention)은 관측보다 더 깊은 수준의 추론을 제공한다. 지능형 에이전트는 다음에 무엇이 발생할 가능성이 높은지를 추정하는 것뿐만 아니라 특정 행동을 수행한다면 어떤 일이 발생할지를 질문할 수 있어야 한다. 행동은 내부 월드 모델(world model)에서 선택된 변수 또는 메커니즘을 변경하는 개입으로 표현할 수 있다. 이를 통해 AGI는 외부 환경에서 실제 행동을 수행하기 전에 가능한 결과를 평가할 수 있다.

반사실적 추론(counterfactual reasoning)은 AGI가 직접 경험하지 않은 가능성으로부터도 학습할 수 있도록 한다. 결과를 관측한 후 시스템은 다른 의사결정을 내렸거나 다른 조건이 존재했다면 사건이 어떻게 전개되었을지를 질문할 수 있다. 이러한 추론은 모든 대안 행동을 물리적으로 반복하지 않고도 설명, 오류 분석(error analysis), 책임 평가(responsibility assessment), 전략 개선 및 이전 경험으로부터의 학습을 지원한다.

인과 월드 모델(causal world model)은 이러한 능력에 필요한 내부 구조를 제공할 수 있다. 미래 관측을 하나의 비분화된 시퀀스(undifferentiated sequence)로 예측하는 대신 객체, 상태, 행동, 관계 및 전이 메커니즘(transition mechanism)을 표현한다. AGI는 이러한 모델을 사용하여 개입을 시뮬레이션하고, 대안적인 미래를 비교하며, 결과를 발생시킨 메커니즘을 식별하고, 예상과 새로운 관측이 일치하지 않을 때 선택된 구성 요소를 갱신할 수 있다.

시간 인과성(temporal causality)은 지능적 행동이 사건의 시퀀스를 통해 전개되기 때문에 필수적이다. 행동은 상태에 영향을 주고, 상태는 이후의 기회에 영향을 주며, 지연된 결과(delayed consequence)는 최초의 의사결정으로부터 상당한 시간이 지난 뒤 나타날 수 있다. AGI는 즉각적인 효과와 후속 결과(downstream consequence)를 구별하고 여러 시간 척도에 걸쳐 작동하는 피드백 루프(feedback loop)를 이해해야 한다. 이를 통해 단기적인 상관관계를 넘어 계획하고 장기 목표를 추론할 수 있다.

다중 모달 인과성(multimodal causality) 역시 중요하다. 일반 지능 시스템은 언어, 비전, 오디오, 촉각, 고유수용감각(proprioception), 구조화 데이터베이스 및 기타 채널을 통해 정보를 받을 수 있기 때문이다. 이러한 관측을 현실에 대한 서로 독립적인 설명으로 취급해서는 안 된다. 이들은 흔히 공유된 기반 원인(shared underlying cause)에서 발생한다. 공통 인과 상태(common causal state)를 통해 이를 통합하면 환경에 대해 더욱 일관되고 강건한 이해를 형성할 수 있다.

인과 발견(causal discovery)을 통해 AGI는 훈련 과정에서 제공된 메커니즘을 넘어 자신의 지식을 확장할 수 있다. 시스템이 익숙하지 않은 환경을 만나면 관계를 관측하고, 안전한 개입을 수행하고, 대안적인 가설을 비교하며, 내부 인과 구조를 수정할 수 있다. 이에 따라 지능은 고정된 사전학습 모델(pretrained model)을 적용하는 것에 머무르지 않고 가설 형성, 증거 수집, 메커니즘 검증, 믿음 갱신(belief updating)이 반복되는 과정이 된다.

능동 학습(active learning)은 이러한 관점에서 자연스럽게 이어진다. AGI는 정보를 수동적으로 수집하거나 무작위로 탐색할 필요가 없다. 현재 목표에서 어떤 불확실성이 중요한지를 식별하고 가장 유용한 증거를 제공할 것으로 예상되는 관측이나 개입을 선택할 수 있다. 이를 통해 탐색(exploration)은 목적을 가진 실험으로 전환되며 익숙하지 않은 시스템을 이해하는 데 필요한 경험의 양을 크게 줄일 수 있다.

인과 일반화(causal generalization)는 환경 사이에서 지식을 전이하는 데 핵심적이다. AGI가 표면적인 특성이 변화하더라도 어떤 메커니즘이 안정적으로 유지된다는 것을 학습한다면 새로운 맥락에서도 해당 메커니즘을 재사용할 수 있다. 기반 인과 구조가 유사하다면 외형, 언어, 위치, 센서 구성 또는 작업 설명이 변화하더라도 모든 것을 완전히 다시 학습할 필요가 없다. 이는 강건한 분포 외 행동(out-of-distribution behavior)을 지원한다.

모듈성(modularity)은 이러한 일반화 능력을 강화한다. 복잡한 환경을 하나의 거대한 예측 함수가 아니라 상호작용하는 인과 메커니즘들의 집합으로 표현할 수 있다. 하나의 메커니즘이 변화하면 AGI는 영향을 받지 않은 지식을 보존하면서 해당 구성 요소만 수정할 수 있다. 이러한 모듈성은 이전에 학습한 메커니즘을 익숙하지 않은 상황에서 재조합할 수 있게 하여 효율적인 적응, 지속 학습(continual learning), 조합적 추론(compositional reasoning)을 지원한다.

조합적 추론(compositional reasoning)은 새로운 문제가 익숙한 요소들의 새로운 조합으로 구성되는 경우가 많기 때문에 일반 지능에서 특히 중요하다. AGI는 개별 객체, 행동, 물리적 원리, 사회적 제약을 이해하면서도 이들이 정확히 같은 조합으로 나타나는 상황을 이전에 경험하지 않았을 수 있다. 인과 표현을 이용하면 가능한 모든 상황의 사례를 암기할 필요 없이 각각의 메커니즘에 따라 이러한 구성 요소를 재조합할 수 있다.

계층적 인과성(hierarchical causality)은 서로 다른 추상화 수준(abstraction level)을 연결할 수 있다. 저수준 메커니즘은 힘, 운동, 신호 또는 신경 계산을 설명할 수 있으며, 상위 수준에서는 객체, 목표, 계획, 조직 및 사회적 상호작용을 표현할 수 있다. AGI는 모든 유용한 설명이 동일한 해상도에 존재한다고 가정하지 않고 이러한 수준을 넘나들며 추론해야 한다. 작업에 따라 서로 다른 인과적 추상화가 필요하지만 이들은 기반 메커니즘과 연결되어 있어야 한다.

언어(language)는 인과 지식(causal knowledge)에 접근하는 강력한 인터페이스를 제공할 수 있다. 인간의 설명에는 이유, 결과, 의도, 조건 및 가상적인 대안이 빈번하게 포함된다. 대규모 언어 모델(Large Language Model, LLM)은 이러한 지식을 추출하고 조작할 수 있지만 언어적 개연성(linguistic plausibility)만으로 인과적 진실을 확립할 수는 없다. AGI는 어떤 설명이 실제로 뒷받침되는지를 판단하기 위해 언어 기반 가설을 관측, 외부 지식, 실험, 도구 및 월드 모델과 연결해야 한다.

기억(memory) 역시 인과 추론과 밀접하게 상호작용한다. 일화 기억(episodic memory)은 특정 경험을 보존하고, 의미 기억(semantic memory)은 여러 사건에서 추출된 일반화된 메커니즘을 저장할 수 있다. AGI는 새로운 상황과 이전 경험을 비교하여 어떤 인과 구조가 여전히 관련되어 있는지를 식별하고, 반복적인 증거가 기존 메커니즘과 모순될 경우 이를 수정할 수 있다. 따라서 기억은 단순한 검색(retrieval)을 넘어 지속적인 인과 모델 구축에 기여한다.

계획(planning)은 가능한 미래에 대한 인과 추론으로 이해할 수 있다. 목표와 제약 조건이 주어지면 AGI는 후보 행동을 생성하고, 내부 월드 모델에 개입을 적용하고, 그 결과 발생하는 상태 전이를 시뮬레이션하여 예상 결과를 비교할 수 있다. 모델이 불확실성과 여러 대안적인 인과 가설을 표현할 수 있다면 계획 능력은 더욱 강력해지며, 에이전트는 목표를 달성하면서 동시에 중요한 불확실성을 줄이는 행동을 선택할 수 있다.

인과 추론은 안전성(safety)도 지원할 수 있다. 높은 능력을 가진 자율 시스템은 설계자가 예상하지 못했던 상황을 만날 수 있으므로 고정된 규칙만으로는 충분하지 않을 수 있다. 행동이 위험 요소로 어떻게 전파되는지를 이해하면 시스템은 안전하지 않은 후속 상태를 발생시키는 계획을 거부할 수 있다. 반사실적 시뮬레이션(counterfactual simulation)을 이용하면 위험한 결과를 직접 경험하지 않고도 내부적으로 위험 가능성을 평가할 수 있다.

사회적 지능(social intelligence)은 다른 에이전트가 자신의 행동에 영향을 주는 목표, 믿음, 지식 및 의도를 가지고 있기 때문에 추가적인 인과적 복잡성을 발생시킨다. 인간과 상호작용하는 AGI는 관측 가능한 행동과 그것을 만들어낼 가능성이 있는 숨겨진 요인을 구별하면서 그러한 요인에 대한 불확실성을 유지해야 한다. 에이전트에 대한 인과 모델은 협력과 의사소통을 지원할 수 있지만, 불확실하게 추론된 의도를 확정된 사실처럼 취급해서는 안 된다.

과학적 추론(scientific reasoning)은 AGI와 인과성 사이의 또 다른 중요한 연결을 보여준다. 과학은 설명을 제안하고, 예측을 도출하며, 실험을 설계하고, 개입을 수행하고, 이론을 수정함으로써 발전한다. 이러한 순환 과정에 참여할 수 있는 AGI는 기존 정보를 단순히 요약하는 것을 넘어 서로 경쟁하는 인과 모델을 비교할 수 있어야 한다. 따라서 인과 추론은 일반 지능을 자율적인 가설 형성(autonomous hypothesis formation) 및 발견(discovery)과 연결한다.

체화된 인공 일반 지능(Embodied AGI)에서는 물리적 행동이 직접적인 개입 데이터를 생성하기 때문에 인과성이 더욱 구체적으로 나타난다. 로봇은 객체를 조작하고, 환경을 이동하며, 결과를 관측하고, 물리적 메커니즘에 대한 이해를 개선할 수 있다. 지각(perception)은 현재 상태를 추정하고, 월드 모델은 결과를 예측하며, 계획은 개입을 평가하고, 제어(control)는 행동을 실행하며, 새로운 관측은 내부 인과 모델을 갱신하기 위한 증거를 제공한다.

이러한 전체 과정에서 불확실성(uncertainty)은 명시적으로 유지되어야 한다. 특히 부분적으로 관측 가능하거나 익숙하지 않은 환경에서는 인과관계를 완전하게 확신할 수 있는 경우가 드물다. AGI는 여러 대안적인 가설을 유지하고, 신뢰도(confidence)를 추정하며, 필요할 경우 추가적인 증거를 탐색하고, 약한 상관관계를 확신에 찬 인과적 결론으로 변환하는 것을 피해야 한다. 따라서 보정된 불확실성(calibrated uncertainty)은 인과적 설명을 구축하는 능력만큼 중요하다.

AGI의 인과 능력을 평가하려면 기존의 벤치마크 정확도(benchmark accuracy)를 넘어서는 검증이 필요하다. 시스템은 개입 추론(intervention reasoning), 반사실적 일관성(counterfactual consistency), 인과 발견, 메커니즘 전이(mechanism transfer), 조합적 일반화, 환경 변화 이후의 적응, 장기 계획(long-horizon planning), 변화된 상관관계에 대한 강건성(robustness)을 기준으로 평가해야 한다. 익숙한 작업에서 높은 성능을 보이더라도 기반 조건이 변화했을 때 실패한다면 일반적인 인과 지능을 입증했다고 보기 어렵다.

인과성은 관측 데이터만으로 항상 복원할 수 없기 때문에 중요한 이론적 한계가 여전히 존재한다. 서로 다른 인과 구조가 동일한 통계적 패턴을 생성할 수 있으며, 숨겨진 교란 요인(hidden confounder)은 그럴듯해 보이는 설명을 잘못된 것으로 만들 수 있다. 따라서 AGI는 단순히 규모(scale)를 확대하는 것만으로 신뢰성 있는 인과 지식을 획득할 수 없다. 많은 인과적 모호성을 해결하기 위해서는 상호작용, 개입, 시간적 증거, 사전 지식(prior knowledge), 실험 설계(experimental design), 명시적인 가정이 여전히 필요하다.

궁극적으로 인공 일반 지능(Artificial General Intelligence, AGI)과 인과성(causality)은 변화하는 세계를 이해하고, 예측하며, 의도적으로 영향을 미칠 수 있는 시스템을 구축한다는 문제에서 서로 연결된다. 인과 표현은 관측을 메커니즘으로 변환하고, 개입은 추론과 행동을 연결하며, 반사실적 추론은 대안적인 미래를 탐색하게 하고, 인과 발견은 지속적인 학습을 가능하게 한다. 이러한 능력들이 결합되면 패턴 기반 지능(pattern-based intelligence)을 넘어 사건이 왜 발생하는지 추론하고 자신의 행동이 다음에 일어날 일을 어떻게 변화시키는지 이해하는 적응형 에이전트(adaptive agent)로 발전할 수 있는 기반을 제공한다.
