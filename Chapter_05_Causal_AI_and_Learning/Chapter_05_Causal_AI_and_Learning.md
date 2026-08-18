**Volume 46. Causality and Scientific AI**


# Chapter 05. Causal AI and Learning

##  

## 05.01. Causal Representation Learning [w/Code]

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal representation learning seeks to learn internal representations that capture the underlying causal factors responsible for observed data rather than merely encoding statistical correlations. Conventional representation learning can discover compact features that are highly predictive within a training distribution, yet these features may depend on accidental correlations. A causal representation instead aims to organize latent variables around mechanisms that generate observations and determine how the world changes.

The central motivation is that observations are often high-dimensional manifestations of a much smaller set of meaningful causal variables. An image may contain millions of pixel values, while its relevant generative factors include object identity, position, orientation, illumination, material, and interactions with other objects. Causal representation learning attempts to infer such variables from raw observations and encode them into a structured latent space where causal relationships become easier to discover and manipulate.

A useful distinction exists between ordinary latent variables and causal latent variables. An autoencoder can compress observations into a low-dimensional vector without assigning causal meaning to individual dimensions. Two latent coordinates may arbitrarily mix several physical factors while still reconstructing the input accurately. Causal representations seek variables whose changes correspond more directly to independent mechanisms, interventions, or stable properties of the underlying system.

This objective is closely related to disentangled representation learning, but the two concepts are not identical. Disentanglement attempts to separate independent factors of variation, whereas causality additionally describes directional relationships among those factors. Variables may be statistically dependent because one causes another, because they share a common cause, or because selection mechanisms connect them. A causal representation therefore requires structural information beyond simple statistical independence.

Structural causal models provide a natural conceptual foundation for this approach. A latent representation can be interpreted as a collection of variables connected through structural equations, where each variable is generated from its causal parents and an associated exogenous disturbance. The resulting latent causal graph describes not only which variables are related but also how changes propagate through the system when particular variables or mechanisms are modified.

Interventions provide especially valuable information for learning causal representations. Observational data reveal how variables coexist under naturally occurring conditions, while interventions deliberately modify part of the system and expose which other variables respond. If changing one latent factor repeatedly produces predictable changes in another while leaving unrelated mechanisms stable, the learning system obtains evidence about causal direction and modular structure that observational correlation alone may not reveal.

Temporal data can provide another source of causal information because causes generally influence future states rather than arbitrary past states. Sequential observations allow models to examine which latent factors persist, which evolve, and which changes precede other changes. In dynamical environments, representations can therefore be trained to encode state variables that support prediction of future trajectories while separating persistent properties from transient disturbances and externally applied actions.

Independent causal mechanisms are an important principle behind many approaches. A complex system can often be understood as a collection of mechanisms that operate relatively independently, even though their outputs interact. If one mechanism changes, other mechanisms may remain valid. Representations organized according to these modules can support adaptation because the model may update the affected component without relearning every relationship encoded in the entire system.

Identifiability is one of the fundamental difficulties of causal representation learning. Many different latent representations can explain exactly the same observational distribution, making it impossible in general to determine the true causal variables from passive data alone. Additional assumptions or information are therefore required, such as temporal structure, multiple environments, known interventions, weak supervision, sparsity, independence assumptions, or knowledge about how the underlying system generates observations.

Multiple environments are particularly useful because causal mechanisms often remain stable while correlations produced by context change. A model trained across different environments can search for representations that preserve invariant relationships rather than features that happen to predict well in only one domain. This idea connects causal representation learning with domain generalization, invariant prediction, transfer learning, and robust machine learning under distribution shifts.

Self-supervised learning can serve as an important practical bridge because causal variables are rarely available as explicit labels. Predicting masked information, future states, transformations, temporal relationships, or cross-modal correspondences can encourage an encoder to discover meaningful structure without exhaustive human annotation. However, self-supervision alone does not guarantee causal representations; objectives and data variations must provide signals capable of distinguishing causal mechanisms from convenient statistical shortcuts.

Generative models offer another important route. A decoder can describe how latent variables generate observations, while an encoder estimates those variables from data. Variational autoencoders, flow-based models, and other latent-variable architectures can be extended with assumptions about causal graphs, interventions, environments, or structured transitions. The learned latent space then becomes not merely a compressed description but a candidate model of the hidden processes responsible for observed phenomena.

Contrastive methods can also contribute when positive and negative pairs are constructed according to meaningful transformations or environmental changes. Observations sharing the same underlying causal factor can be encouraged to have similar representations while irrelevant variations are separated or suppressed. The effectiveness of this strategy depends strongly on how pairs are generated, because poorly chosen augmentation rules can accidentally remove causal information or preserve undesirable shortcuts.

Causal representation learning becomes especially important when an AI system must operate outside its training distribution. A purely correlational representation may fail when background conditions, sensor properties, environmental statistics, or operational contexts change. Representations based on stable causal mechanisms can potentially distinguish what has changed from what remains structurally valid, allowing downstream predictors and decision systems to reuse knowledge rather than treating every new environment as an unrelated problem.

For robotics and embodied AI, causal representations can describe properties such as object state, robot configuration, contact, motion, force, affordance, and environmental dynamics. An agent does not merely observe these variables; its actions intervene on them. Pushing an object, opening a door, accelerating a vehicle, or grasping a tool produces controlled changes that reveal causal structure. Interactive agents therefore possess a powerful source of causal supervision through their own actions.

A robot world model can exploit this structure by encoding observations into latent causal states, applying candidate actions as interventions, and predicting resulting state transitions. Instead of asking only what is likely to happen next, the model can estimate what would happen if a particular action were executed. Such representations connect perception, prediction, planning, and control and provide a foundation for counterfactual simulation before potentially costly or dangerous actions are performed.

Multimodal observations further strengthen this framework because causal factors often produce simultaneous effects across several sensing channels. Motion may appear in camera images, LiDAR geometry, inertial measurements, joint encoders, and force sensors in different forms. Learning a shared causal representation can separate sensor-specific appearance from common physical causes, allowing multimodal systems to reason about the underlying state rather than treating each sensor stream as an independent statistical signal.

Evaluation remains difficult because good predictive accuracy does not prove that a representation is causal. Evaluation may instead examine whether latent variables correspond to known generative factors, whether interventions produce correct downstream changes, whether mechanisms remain stable across environments, and whether representations support transfer under distribution shift. Counterfactual prediction and intervention generalization provide particularly demanding tests because they require knowledge beyond ordinary observational fitting.

Causal representation learning ultimately attempts to move machine learning from recognizing recurring patterns toward modeling the mechanisms that produce those patterns. Its promise lies in representations that are interpretable, modular, transferable, intervention-aware, and robust to changing environments. Within causal AI, it forms a bridge between raw high-dimensional perception and explicit causal reasoning, providing structured variables upon which causal deep learning, causal reinforcement learning, causal world models, and more general reasoning systems can operate.

인과 표현 학습(Causal Representation Learning)은 관측 데이터에서 나타나는 통계적 상관관계(statistical correlation)를 단순히 부호화하는 것이 아니라, 관측 데이터를 발생시키는 근본적인 인과 요인(causal factor)을 포착하는 내부 표현(internal representation)을 학습하는 것을 목표로 한다. 일반적인 표현 학습(representation learning)은 훈련 분포(training distribution) 내에서 높은 예측력을 갖는 압축된 특징을 발견할 수 있지만, 이러한 특징은 우연한 상관관계에 의존할 수 있다. 반면 인과 표현(causal representation)은 관측을 생성하고 세계가 어떻게 변화하는지를 결정하는 메커니즘(mechanism)을 중심으로 잠재 변수를 구성하려 한다.

핵심적인 동기는 관측 데이터가 흔히 소수의 의미 있는 인과 변수(causal variable)가 만들어낸 고차원적 표현이라는 점에 있다. 하나의 이미지는 수백만 개의 픽셀 값을 포함할 수 있지만, 실제로 중요한 생성 요인(generative factor)은 객체 정체성(object identity), 위치(position), 방향(orientation), 조명(illumination), 재질(material), 다른 객체와의 상호작용(interaction) 등이다. 인과 표현 학습은 이러한 변수를 원시 관측(raw observation)으로부터 추론하고, 인과관계를 보다 쉽게 발견하고 조작할 수 있는 구조화된 잠재 공간(structured latent space)에 부호화하려 한다.

일반적인 잠재 변수(latent variable)와 인과 잠재 변수(causal latent variable)는 구분할 필요가 있다. 오토인코더(autoencoder)는 각각의 차원에 인과적 의미를 부여하지 않고도 관측을 저차원 벡터(low-dimensional vector)로 압축할 수 있다. 두 개의 잠재 좌표(latent coordinate)가 여러 물리적 요인을 임의로 혼합하면서도 입력을 정확하게 복원할 수 있다. 인과 표현은 각 변수의 변화가 독립적인 메커니즘(independent mechanism), 개입(intervention), 또는 기반 시스템의 안정적인 속성과 보다 직접적으로 대응하도록 만드는 것을 목표로 한다.

이러한 목표는 얽힘 해소 표현 학습(disentangled representation learning)과 밀접하게 관련되지만 두 개념이 동일한 것은 아니다. 얽힘 해소(disentanglement)는 서로 독립적인 변동 요인(factor of variation)을 분리하려는 반면, 인과성(causality)은 이러한 요인들 사이의 방향성 관계(directional relationship)를 추가적으로 설명한다. 변수들은 하나가 다른 하나를 원인으로 만들거나, 공통 원인(common cause)을 공유하거나, 선택 메커니즘(selection mechanism)에 의해 연결되어 통계적으로 의존할 수 있다. 따라서 인과 표현에는 단순한 통계적 독립성(statistical independence)을 넘어서는 구조적 정보(structural information)가 필요하다.

구조적 인과 모델(Structural Causal Model, SCM)은 이러한 접근법에 자연스러운 개념적 기반을 제공한다. 잠재 표현(latent representation)은 구조 방정식(structural equation)으로 연결된 변수들의 집합으로 해석할 수 있으며, 각각의 변수는 자신의 인과 부모(causal parent)와 외생 교란(exogenous disturbance)에 의해 생성된다. 이렇게 만들어진 잠재 인과 그래프(latent causal graph)는 어떤 변수들이 서로 관련되어 있는지를 나타낼 뿐만 아니라, 특정 변수나 메커니즘이 변경되었을 때 그 변화가 시스템을 통해 어떻게 전파되는지도 설명한다.

개입(intervention)은 인과 표현을 학습하는 데 특히 중요한 정보를 제공한다. 관측 데이터(observational data)는 자연적인 조건에서 변수들이 어떻게 함께 나타나는지를 보여주는 반면, 개입은 시스템의 일부를 의도적으로 변경하여 다른 변수들이 어떻게 반응하는지를 드러낸다. 하나의 잠재 요인(latent factor)을 반복적으로 변경했을 때 다른 요인에서 예측 가능한 변화가 발생하면서 관련 없는 메커니즘은 안정적으로 유지된다면, 학습 시스템은 단순한 관측 상관관계만으로는 알아내기 어려운 인과 방향(causal direction)과 모듈 구조(modular structure)에 대한 증거를 얻을 수 있다.

시간 데이터(temporal data)는 원인이 일반적으로 임의의 과거 상태가 아니라 미래 상태에 영향을 준다는 점에서 또 다른 인과 정보의 원천이 될 수 있다. 순차 관측(sequential observation)을 이용하면 어떤 잠재 요인이 지속되고, 어떤 요인이 변화하며, 어떤 변화가 다른 변화보다 먼저 발생하는지를 분석할 수 있다. 따라서 동적 환경(dynamic environment)에서는 미래 궤적(future trajectory)을 예측할 수 있는 상태 변수를 부호화하면서 지속적인 속성과 일시적인 교란, 외부에서 적용된 행동을 분리하도록 표현을 학습할 수 있다.

독립 인과 메커니즘(Independent Causal Mechanisms)은 많은 인과 표현 학습 접근법의 중요한 원리이다. 복잡한 시스템은 출력이 서로 상호작용하더라도 비교적 독립적으로 작동하는 여러 메커니즘의 집합으로 이해할 수 있다. 하나의 메커니즘이 변경되더라도 다른 메커니즘은 계속 유효할 수 있다. 이러한 모듈에 따라 표현을 구성하면 전체 시스템의 모든 관계를 다시 학습하지 않고 영향을 받은 구성 요소만 갱신할 수 있기 때문에 적응(adaptation)에 유리하다.

식별 가능성(identifiability)은 인과 표현 학습의 근본적인 어려움 가운데 하나이다. 서로 다른 여러 잠재 표현이 동일한 관측 분포(observational distribution)를 설명할 수 있기 때문에, 일반적으로 수동적인 관측 데이터만으로 실제 인과 변수를 결정하는 것은 불가능하다. 따라서 시간적 구조(temporal structure), 다중 환경(multiple environments), 알려진 개입(known intervention), 약한 지도 학습(weak supervision), 희소성(sparsity), 독립성 가정(independence assumption), 또는 시스템이 관측을 생성하는 방식에 대한 지식과 같은 추가적인 가정이나 정보가 필요하다.

다중 환경(multiple environments)은 상황에 의해 만들어진 상관관계가 변화하더라도 인과 메커니즘은 안정적으로 유지되는 경우가 많기 때문에 특히 유용하다. 서로 다른 환경에서 학습된 모델은 하나의 도메인(domain)에서만 우연히 높은 예측력을 갖는 특징 대신, 환경이 달라져도 유지되는 불변 관계(invariant relationship)를 탐색할 수 있다. 이러한 개념은 인과 표현 학습을 도메인 일반화(domain generalization), 불변 예측(invariant prediction), 전이 학습(transfer learning), 분포 변화(distribution shift)에 강건한 머신러닝(robust machine learning)과 연결한다.

자기지도 학습(self-supervised learning)은 인과 변수가 명시적인 레이블(label)로 제공되는 경우가 드물다는 점에서 중요한 실용적 연결고리가 될 수 있다. 마스킹된 정보(masked information), 미래 상태(future state), 변환(transformation), 시간적 관계(temporal relationship), 또는 교차 모달 대응(cross-modal correspondence)을 예측하도록 학습하면 방대한 인간 주석 없이도 인코더(encoder)가 의미 있는 구조를 발견하도록 유도할 수 있다. 그러나 자기지도 학습 자체가 인과 표현을 보장하는 것은 아니며, 학습 목표와 데이터 변화가 인과 메커니즘과 단순한 통계적 지름길(statistical shortcut)을 구별할 수 있는 신호를 제공해야 한다.

생성 모델(generative model)은 또 다른 중요한 접근 경로를 제공한다. 디코더(decoder)는 잠재 변수가 어떻게 관측을 생성하는지를 표현하고, 인코더(encoder)는 데이터로부터 이러한 변수를 추정할 수 있다. 변이형 오토인코더(Variational Autoencoder, VAE), 플로 기반 모델(flow-based model) 및 기타 잠재 변수 아키텍처(latent-variable architecture)는 인과 그래프, 개입, 환경 또는 구조화된 상태 전이(structured transition)에 관한 가정을 포함하도록 확장될 수 있다. 이렇게 학습된 잠재 공간은 단순한 압축 표현을 넘어 관측 현상을 만들어내는 숨겨진 과정의 후보 모델이 된다.

대조 학습(contrastive learning) 역시 양성 쌍(positive pair)과 음성 쌍(negative pair)이 의미 있는 변환이나 환경 변화에 따라 구성될 경우 인과 표현 학습에 기여할 수 있다. 동일한 기반 인과 요인을 공유하는 관측은 유사한 표현을 갖도록 만들고, 관련 없는 변동은 분리하거나 억제할 수 있다. 그러나 이 전략의 효과는 데이터 쌍이 어떻게 생성되는지에 크게 의존하며, 잘못 선택된 데이터 증강(data augmentation) 규칙은 중요한 인과 정보를 제거하거나 바람직하지 않은 통계적 지름길을 유지할 수 있다.

인과 표현 학습은 인공지능 시스템이 훈련 분포 외부(out-of-distribution)에서 동작해야 할 때 특히 중요해진다. 순수한 상관관계 기반 표현은 배경 조건, 센서 특성, 환경 통계 또는 운영 상황이 변화하면 실패할 수 있다. 안정적인 인과 메커니즘에 기반한 표현은 무엇이 변화했고 무엇이 구조적으로 유지되는지를 구분할 가능성이 있으며, 이를 통해 후속 예측 시스템과 의사결정 시스템은 새로운 환경을 완전히 별개의 문제로 취급하지 않고 기존 지식을 재사용할 수 있다.

로보틱스(robotics)와 체화 인공지능(embodied AI)에서 인과 표현은 객체 상태(object state), 로봇 구성(robot configuration), 접촉(contact), 운동(motion), 힘(force), 행동유도성(affordance), 환경 동역학(environmental dynamics)과 같은 속성을 표현할 수 있다. 에이전트(agent)는 이러한 변수들을 단순히 관측하는 것이 아니라 자신의 행동을 통해 직접 개입한다. 물체를 밀거나, 문을 열거나, 차량을 가속하거나, 도구를 잡는 행동은 통제된 상태 변화를 발생시켜 인과 구조를 드러낸다. 따라서 상호작용형 에이전트(interactive agent)는 자신의 행동 자체를 통해 강력한 인과 지도 신호(causal supervision)를 얻을 수 있다.

로봇 월드 모델(robot world model)은 이러한 구조를 활용하여 관측을 잠재 인과 상태(latent causal state)로 부호화하고, 후보 행동(candidate action)을 개입으로 적용한 뒤 그 결과로 발생할 상태 전이(state transition)를 예측할 수 있다. 모델은 단순히 다음에 무엇이 발생할 가능성이 높은지를 묻는 것을 넘어, 특정 행동을 실행한다면 무엇이 발생할지를 추정할 수 있다. 이러한 표현은 지각(perception), 예측(prediction), 계획(planning), 제어(control)를 연결하며 비용이 크거나 위험할 수 있는 행동을 실제로 수행하기 전에 반사실적 시뮬레이션(counterfactual simulation)을 수행할 수 있는 기반을 제공한다.

다중 모달 관측(multimodal observation)은 하나의 인과 요인이 여러 센싱 채널(sensing channel)에 동시에 영향을 미치는 경우가 많기 때문에 이러한 프레임워크를 더욱 강화한다. 운동은 카메라 영상, 라이다(LiDAR) 기하 구조, 관성 측정(inertial measurement), 관절 인코더(joint encoder), 힘 센서(force sensor)에 서로 다른 형태로 나타날 수 있다. 공유 인과 표현(shared causal representation)을 학습하면 센서별 표현 차이를 공통된 물리적 원인과 분리하여, 다중 모달 시스템이 각각의 센서 스트림을 독립적인 통계 신호로 취급하는 대신 기반 상태 자체를 추론하도록 만들 수 있다.

평가(evaluation)는 높은 예측 정확도만으로 표현이 인과적이라는 사실을 증명할 수 없기 때문에 여전히 어렵다. 대신 잠재 변수가 알려진 생성 요인과 대응하는지, 개입이 올바른 후속 변화를 발생시키는지, 메커니즘이 서로 다른 환경에서도 안정적으로 유지되는지, 그리고 표현이 분포 변화에서 전이(transfer)를 지원하는지를 평가할 수 있다. 특히 반사실적 예측(counterfactual prediction)과 개입 일반화(intervention generalization)는 일반적인 관측 데이터 적합을 넘어서는 지식을 요구하기 때문에 매우 엄격한 평가 기준이 된다.

궁극적으로 인과 표현 학습(Causal Representation Learning)은 머신러닝(machine learning)을 반복적으로 나타나는 패턴을 인식하는 단계에서 그러한 패턴을 생성하는 메커니즘 자체를 모델링하는 단계로 발전시키려는 접근이다. 그 핵심 가능성은 해석 가능하고(interpretable), 모듈화되며(modular), 전이 가능하고(transferable), 개입을 이해하며(intervention-aware), 변화하는 환경에 강건한(robust) 표현에 있다. 인과 인공지능(causal AI)에서 이는 고차원 원시 지각(raw high-dimensional perception)과 명시적인 인과 추론(causal reasoning)을 연결하며, 인과 딥러닝(causal deep learning), 인과 강화학습(causal reinforcement learning), 인과 월드 모델(causal world model), 그리고 보다 일반적인 추론 시스템이 작동할 수 있는 구조화된 변수를 제공한다.

##  

## 05.02. Causal Deep Learning

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal deep learning combines the representation power of deep neural networks with explicit principles of causal reasoning. Conventional deep learning is exceptionally effective at discovering statistical patterns in large datasets, but prediction alone does not reveal why an outcome occurs or how it would change under intervention. Causal deep learning seeks neural models that represent causes, mechanisms, interventions, and counterfactual relationships while retaining the scalability of modern deep architectures.

The distinction between correlation and causation becomes especially important when neural networks operate outside their training conditions. A model may learn that two variables frequently appear together without understanding the mechanism connecting them. When the environment changes, such correlations may disappear. Incorporating causal structure encourages models to rely on relationships that remain meaningful across environments rather than shortcuts that happen to perform well on the original training distribution.

A causal deep learning system can be viewed as combining neural representation learning with a structural causal model. Neural encoders transform high-dimensional observations into latent variables, while causal relationships among those variables describe how different components of the system influence one another. Neural networks can also parameterize structural equations, allowing nonlinear and highly complex causal mechanisms to be represented while preserving an explicit distinction between causes and their effects.

This combination is valuable because classical causal models often assume relatively compact variables that have already been defined by researchers. Real-world AI systems instead receive images, video, language, LiDAR, audio, biological signals, or large collections of sensor measurements. Deep networks can extract useful latent variables from these observations, while causal modeling organizes the resulting representations into mechanisms suitable for intervention, explanation, prediction, and decision making.

Intervention is a defining concept in causal deep learning. Ordinary prediction estimates an outcome conditioned on observed information, whereas intervention asks what would happen if a variable were deliberately changed. Neural models can be trained using observational and interventional datasets so that they distinguish naturally occurring associations from externally imposed changes. This distinction enables systems to predict consequences of actions rather than merely extrapolate correlations found in historical observations.

Counterfactual reasoning extends this capability by considering alternative outcomes for events that have already occurred. After estimating the latent state and causal mechanisms responsible for an observation, a model can modify one causal variable while holding relevant background conditions fixed. It can then simulate an alternative outcome, supporting questions such as what would have happened under another treatment, control action, environmental condition, or operational decision.

Causal regularization provides one practical method for introducing causal assumptions into neural learning. Training objectives can encourage invariance, sparsity, modularity, independence of mechanisms, or consistency under intervention. Instead of optimizing only prediction or reconstruction error, the model is penalized when its internal representations violate desired causal properties. These additional constraints guide learning toward representations that may generalize more reliably than unconstrained statistical features.

Invariant learning is particularly important for causal deep networks. If a relationship represents a stable causal mechanism, it should often remain useful when background conditions or environmental distributions change. Training across multiple domains can therefore encourage the network to identify features whose predictive relationships remain stable. Spurious correlations that vary across environments become less attractive, while persistent mechanisms receive greater importance in the learned representation.

Domain shifts illustrate why this matters. An image classifier may associate a particular background with an object because the two frequently coexist in the training dataset. A causal approach attempts to separate properties responsible for the object\'s identity from contextual variables that merely correlate with it. Similar problems occur in medicine, autonomous driving, industrial inspection, finance, robotics, and scientific modeling whenever deployment conditions differ from historical training data.

Attention mechanisms can also participate in causal deep learning, although attention itself should not be interpreted automatically as causality. Attention identifies information that a model considers useful for its computation, whereas causal influence concerns how changing one variable changes another. Causal constraints, interventions, or graph structures can be combined with attention so that information selection is informed by candidate causal relationships rather than purely predictive relevance.

Graph neural networks provide a natural architecture when causal variables and their relationships can be represented as nodes and directed connections. Message passing can model interactions among variables, components, agents, or physical entities, while structural constraints specify which directions of influence are permitted. Neural causal graphs can therefore combine relational learning with causal structure and are useful for complex systems whose topology plays an important role in their behavior.

Generative deep models provide another route toward causal modeling. Variational autoencoders and related architectures can represent latent causal factors and generate observations from them. By incorporating causal graphs or structured mechanisms into the latent space, the model can generate not only statistically plausible samples but also samples corresponding to interventions. This allows the generative process to answer how observations might change when particular underlying causes are modified.

Temporal neural networks are especially relevant because many causal processes unfold dynamically. Recurrent networks, temporal convolutional networks, Transformers, and state-space models can learn relationships among sequences of latent states. When combined with causal assumptions, they can distinguish persistent state, external intervention, system dynamics, and environmental disturbance, providing a richer description than ordinary sequence prediction based only on temporal correlation.

Causal deep learning also connects strongly with self-supervised learning. Large quantities of unlabeled data can be used to learn representations through future prediction, masked reconstruction, cross-modal alignment, or transformation prediction. Causal constraints can then encourage these representations to correspond to stable mechanisms rather than arbitrary predictive features. This combination is attractive because explicit causal labels are difficult to obtain, while observational and sequential data are abundant.

In robotics, causal deep learning naturally integrates perception and action. A robot observes the environment through cameras, LiDAR, force sensors, proprioception, and other modalities, while its motor commands actively modify the environment. Actions therefore provide intervention signals. A model can learn which state changes result from its own actions, which arise from external agents, and which reflect environmental dynamics, improving planning and control in interactive physical environments.

Causal world models extend this idea by learning structured internal models of environment dynamics. The model encodes the current observation into a latent state, represents actions as interventions, and predicts possible future states. Planning can then compare alternative action sequences before execution. Rather than relying solely on statistical trajectory prediction, the system attempts to represent how specific actions cause changes in objects, agents, and environmental conditions.

Autonomous systems benefit from this capability because safety often depends on reasoning about consequences rather than simply predicting likely events. An autonomous vehicle, for example, must distinguish between observing another vehicle slowing down and understanding how its own acceleration, braking, or lane change could alter future interactions. Causal deep models can support intervention-aware prediction, enabling planners to evaluate possible actions within a structured model of dynamic relationships.

Scientific AI provides another important application. Deep networks can approximate complicated nonlinear relationships in physical, biological, chemical, or engineering systems, while causal structures encode hypotheses about underlying mechanisms. Experimental interventions can then test whether learned relationships behave consistently with the proposed causal model. This creates a connection between data-driven discovery and scientific reasoning, where models are expected not only to predict observations but also to support mechanistic explanations.

Interpretability can improve when neural representations are connected to explicit causal variables and mechanisms. Traditional neural networks may distribute information across many hidden units without assigning clear meaning to them. A causal architecture attempts to organize relevant information according to variables, mechanisms, and directed dependencies. Explanations can therefore focus on which causes influenced an outcome and how changes to those causes would alter the predicted result.

Evaluation of causal deep learning requires more than conventional predictive accuracy. Models should be tested under interventions, distribution shifts, unseen environments, and counterfactual scenarios. Researchers can examine whether predicted intervention effects match actual outcomes, whether causal mechanisms remain stable across domains, and whether learned representations support transfer to new tasks. Strong performance on ordinary test data may otherwise conceal dependence on fragile correlations.

A major challenge is that causal structure cannot generally be recovered from observational data without assumptions. Deep neural networks do not remove this fundamental limitation. Greater model capacity may actually allow more alternative explanations of the same data. Effective causal deep learning therefore depends on appropriate inductive biases, environmental variation, interventions, temporal information, domain knowledge, or other constraints capable of reducing causal ambiguity.

Causal deep learning ultimately aims to transform deep networks from powerful pattern recognition systems into models capable of reasoning about mechanisms and consequences. By combining neural representation learning with structural causality, intervention, invariance, and counterfactual reasoning, it provides a pathway toward AI systems that can generalize beyond familiar data, explain outcomes, predict the consequences of actions, and support robust decision making in changing environments.

인과 딥러닝(Causal Deep Learning)은 딥 신경망(deep neural network)의 강력한 표현 능력과 명시적인 인과 추론(causal reasoning)의 원리를 결합한다. 기존 딥러닝(conventional deep learning)은 대규모 데이터셋에서 통계적 패턴(statistical pattern)을 발견하는 데 매우 효과적이지만, 예측만으로는 어떤 결과가 왜 발생했는지 또는 개입(intervention)에 의해 결과가 어떻게 달라지는지를 설명하지 못한다. 인과 딥러닝은 현대 딥러닝 아키텍처의 확장성을 유지하면서 원인, 메커니즘, 개입 및 반사실적 관계(counterfactual relationship)를 표현하는 신경 모델을 구축하는 것을 목표로 한다.

상관관계(correlation)와 인과관계(causation)의 구분은 신경망이 훈련 조건을 벗어난 환경에서 동작할 때 특히 중요해진다. 모델은 두 변수가 자주 함께 나타난다는 사실을 학습할 수 있지만, 이들을 연결하는 메커니즘을 이해하지 못할 수 있다. 환경이 변화하면 이러한 상관관계는 사라질 수 있다. 인과 구조(causal structure)를 도입하면 원래의 훈련 분포에서 우연히 잘 작동하는 지름길(shortcut) 대신 환경이 변해도 의미를 유지하는 관계를 학습하도록 모델을 유도할 수 있다.

인과 딥러닝 시스템은 신경 표현 학습(neural representation learning)과 구조적 인과 모델(Structural Causal Model, SCM)을 결합한 형태로 볼 수 있다. 신경 인코더(neural encoder)는 고차원 관측을 잠재 변수(latent variable)로 변환하고, 이러한 변수 사이의 인과관계는 시스템의 여러 구성 요소가 서로 어떻게 영향을 주는지를 설명한다. 신경망은 구조 방정식(structural equation)을 매개변수화하여 원인과 결과의 명시적 구분을 유지하면서 비선형적이고 매우 복잡한 인과 메커니즘을 표현할 수도 있다.

이러한 결합이 중요한 이유는 고전적 인과 모델(classical causal model)이 연구자가 이미 정의한 비교적 간결한 변수를 가정하는 경우가 많기 때문이다. 실제 인공지능 시스템은 이미지, 비디오, 언어, 라이다(LiDAR), 오디오, 생체 신호 또는 대규모 센서 측정 데이터를 입력으로 받는다. 딥 신경망은 이러한 관측으로부터 유용한 잠재 변수를 추출하고, 인과 모델링(causal modeling)은 그 표현을 개입, 설명, 예측 및 의사결정에 사용할 수 있는 메커니즘으로 구성한다.

개입(intervention)은 인과 딥러닝을 정의하는 핵심 개념이다. 일반적인 예측은 관측된 정보를 조건으로 결과를 추정하지만, 개입은 특정 변수를 의도적으로 변경한다면 어떤 일이 발생할지를 묻는다. 신경 모델은 관측 데이터(observational data)와 개입 데이터(interventional data)를 함께 이용하여 자연적으로 발생한 연관성과 외부에서 의도적으로 발생시킨 변화를 구별하도록 학습될 수 있다. 이를 통해 시스템은 과거 데이터의 상관관계를 단순히 외삽하는 대신 행동의 결과를 예측할 수 있다.

반사실적 추론(counterfactual reasoning)은 이미 발생한 사건에 대해 다른 결과를 고려함으로써 이러한 능력을 더욱 확장한다. 관측을 발생시킨 잠재 상태(latent state)와 인과 메커니즘을 추정한 후, 모델은 관련된 배경 조건을 고정하면서 하나의 인과 변수만 변경할 수 있다. 이후 대안적인 결과를 시뮬레이션하여 다른 치료, 제어 행동, 환경 조건 또는 운영 의사결정을 선택했다면 어떤 일이 발생했을지를 분석할 수 있다.

인과 정규화(causal regularization)는 신경망 학습에 인과적 가정을 도입하는 실용적인 방법 가운데 하나이다. 학습 목적 함수(training objective)는 불변성(invariance), 희소성(sparsity), 모듈성(modularity), 메커니즘의 독립성(independence of mechanisms), 또는 개입에 대한 일관성을 장려하도록 구성할 수 있다. 모델은 예측이나 복원 오차만 최소화하는 것이 아니라 내부 표현이 원하는 인과적 특성을 위반할 때 추가적인 페널티를 받으며, 이를 통해 제약되지 않은 통계적 특징보다 일반화 가능성이 높은 표현을 학습하도록 유도된다.

불변 학습(invariant learning)은 인과 딥 신경망에서 특히 중요하다. 어떤 관계가 안정적인 인과 메커니즘을 나타낸다면 배경 조건이나 환경 분포가 변화해도 유용성을 유지해야 하는 경우가 많다. 따라서 여러 도메인(domain)에서 학습하면 신경망이 예측 관계가 안정적으로 유지되는 특징을 찾도록 유도할 수 있다. 환경에 따라 달라지는 허위 상관관계(spurious correlation)의 중요성은 감소하고, 지속적으로 유지되는 메커니즘은 학습된 표현에서 더 큰 중요성을 갖게 된다.

도메인 변화(domain shift)는 이러한 접근이 왜 중요한지를 잘 보여준다. 이미지 분류기는 훈련 데이터에서 특정 배경과 객체가 자주 함께 등장한다는 이유로 둘을 연관시킬 수 있다. 인과적 접근법은 객체의 정체성을 결정하는 속성과 단순히 함께 나타나는 맥락 변수(contextual variable)를 분리하려 한다. 의료, 자율주행, 산업 검사, 금융, 로보틱스 및 과학 모델링에서도 실제 배포 조건이 과거 훈련 데이터와 달라질 때 유사한 문제가 발생한다.

어텐션 메커니즘(attention mechanism)도 인과 딥러닝에 활용될 수 있지만, 어텐션 자체를 자동으로 인과성으로 해석해서는 안 된다. 어텐션은 모델이 계산 과정에서 유용하다고 판단하는 정보를 식별하는 반면, 인과 영향(causal influence)은 하나의 변수를 변경했을 때 다른 변수가 어떻게 변화하는지를 의미한다. 인과 제약(causal constraint), 개입 또는 그래프 구조를 어텐션과 결합하면 단순한 예측 관련성이 아니라 후보 인과관계를 기반으로 정보를 선택하도록 만들 수 있다.

그래프 신경망(Graph Neural Network, GNN)은 인과 변수와 그 관계를 노드(node)와 방향성 연결(directed connection)로 표현할 수 있을 때 자연스러운 아키텍처를 제공한다. 메시지 패싱(message passing)은 변수, 구성 요소, 에이전트 또는 물리적 객체 사이의 상호작용을 모델링하고, 구조적 제약은 허용되는 영향의 방향을 지정할 수 있다. 따라서 신경 인과 그래프(neural causal graph)는 관계 학습과 인과 구조를 결합할 수 있으며 시스템의 위상 구조(topology)가 행동에 중요한 역할을 하는 복잡한 시스템에 유용하다.

생성 딥 모델(generative deep model)은 인과 모델링으로 가는 또 다른 경로를 제공한다. 변이형 오토인코더(Variational Autoencoder, VAE)와 관련 아키텍처는 잠재 인과 요인(latent causal factor)을 표현하고 이를 이용하여 관측을 생성할 수 있다. 잠재 공간(latent space)에 인과 그래프 또는 구조화된 메커니즘을 도입하면 통계적으로 그럴듯한 샘플뿐만 아니라 특정 개입에 대응하는 샘플도 생성할 수 있다. 이를 통해 생성 과정 자체가 특정 근본 원인이 변경될 때 관측이 어떻게 달라지는지를 표현할 수 있다.

시간 신경망(temporal neural network)은 많은 인과 과정이 시간에 따라 동적으로 전개되기 때문에 특히 중요하다. 순환 신경망(Recurrent Neural Network, RNN), 시간 합성곱 신경망(Temporal Convolutional Network, TCN), 트랜스포머(Transformer), 상태 공간 모델(State-Space Model, SSM)은 연속적인 잠재 상태 사이의 관계를 학습할 수 있다. 인과적 가정과 결합하면 지속 상태, 외부 개입, 시스템 동역학 및 환경 교란을 구분하여 단순한 시간적 상관관계에 기반한 순차 예측보다 풍부한 시스템 표현을 제공할 수 있다.

인과 딥러닝은 자기지도 학습(self-supervised learning)과도 밀접하게 연결된다. 대규모 비라벨 데이터(unlabeled data)를 미래 예측, 마스킹 복원(masked reconstruction), 교차 모달 정렬(cross-modal alignment), 변환 예측(transformation prediction) 등에 활용하여 표현을 학습할 수 있다. 이후 인과 제약을 적용하면 이러한 표현이 임의의 예측 특징이 아니라 안정적인 메커니즘에 대응하도록 유도할 수 있다. 명시적인 인과 레이블은 확보하기 어렵지만 관측 데이터와 순차 데이터는 풍부하다는 점에서 이러한 결합은 매우 유용하다.

로보틱스(robotics)에서 인과 딥러닝은 지각(perception)과 행동(action)을 자연스럽게 통합한다. 로봇은 카메라, 라이다, 힘 센서, 고유수용감각(proprioception) 및 다양한 센서를 통해 환경을 관측하는 동시에 모터 명령을 이용하여 환경을 적극적으로 변화시킨다. 따라서 행동 자체가 개입 신호(intervention signal)가 된다. 모델은 자신의 행동에 의해 발생한 상태 변화, 외부 에이전트에 의한 변화, 환경 동역학에 의한 변화를 구별하도록 학습할 수 있으며, 이를 통해 상호작용하는 물리적 환경에서 계획과 제어 성능을 향상시킬 수 있다.

인과 월드 모델(causal world model)은 구조화된 환경 동역학의 내부 모델을 학습함으로써 이러한 개념을 확장한다. 모델은 현재 관측을 잠재 상태로 부호화하고, 행동을 개입으로 표현하며, 가능한 미래 상태를 예측한다. 계획 시스템은 실제 행동을 실행하기 전에 여러 행동 시퀀스(action sequence)를 비교할 수 있다. 단순한 통계적 궤적 예측에 의존하는 대신 특정 행동이 객체, 에이전트 및 환경 조건에 어떤 변화를 일으키는지를 표현하려 한다.

자율 시스템(autonomous system)은 안전성이 단순히 발생 가능성이 높은 사건을 예측하는 것이 아니라 행동의 결과를 추론하는 능력에 의존하기 때문에 이러한 기능의 혜택을 받을 수 있다. 예를 들어 자율주행차는 다른 차량이 감속하는 것을 관측하는 것과 자신의 가속, 제동 또는 차선 변경이 미래의 상호작용을 어떻게 변화시키는지를 이해하는 것을 구별해야 한다. 인과 딥 모델은 개입 인식 예측(intervention-aware prediction)을 지원하여 계획 시스템이 동적 관계의 구조화된 모델 안에서 가능한 행동을 평가하도록 할 수 있다.

과학 인공지능(Scientific AI)은 또 하나의 중요한 응용 분야이다. 딥 신경망은 물리, 생물학, 화학 또는 공학 시스템의 복잡한 비선형 관계를 근사할 수 있고, 인과 구조는 그 기반 메커니즘에 관한 가설을 표현할 수 있다. 실험적 개입(experimental intervention)을 통해 학습된 관계가 제안된 인과 모델과 일관되게 작동하는지 검증할 수 있다. 이는 모델이 관측을 예측할 뿐만 아니라 메커니즘에 기반한 설명을 제공해야 하는 데이터 기반 발견(data-driven discovery)과 과학적 추론(scientific reasoning)을 연결한다.

신경 표현이 명시적인 인과 변수 및 메커니즘과 연결되면 해석 가능성(interpretability)도 향상될 수 있다. 기존 신경망은 명확한 의미를 부여하지 않은 채 많은 은닉 유닛(hidden unit)에 정보를 분산시킬 수 있다. 인과 아키텍처(causal architecture)는 관련 정보를 변수, 메커니즘 및 방향성 의존관계(directed dependency)에 따라 구성하려 한다. 따라서 설명은 어떤 원인이 결과에 영향을 주었는지, 그리고 그 원인을 변경하면 예측 결과가 어떻게 달라지는지에 초점을 맞출 수 있다.

인과 딥러닝의 평가(evaluation)에는 일반적인 예측 정확도 이상의 기준이 필요하다. 모델은 개입, 분포 변화(distribution shift), 보지 못한 환경(unseen environment), 반사실적 시나리오(counterfactual scenario)에서 평가되어야 한다. 예측된 개입 효과가 실제 결과와 일치하는지, 인과 메커니즘이 여러 도메인에서 안정적으로 유지되는지, 학습된 표현이 새로운 작업으로의 전이(transfer)를 지원하는지를 분석할 수 있다. 일반적인 테스트 데이터에서 높은 성능을 보이더라도 취약한 상관관계에 의존하고 있을 가능성이 있기 때문이다.

중요한 과제는 특정한 가정 없이 관측 데이터만으로 인과 구조를 일반적으로 복원할 수 없다는 점이다. 딥 신경망이 이러한 근본적인 한계를 제거해 주는 것은 아니다. 오히려 모델의 표현 능력이 커지면 동일한 데이터를 설명할 수 있는 대안적인 설명도 더욱 많아질 수 있다. 따라서 효과적인 인과 딥러닝은 적절한 귀납적 편향(inductive bias), 환경 변화, 개입, 시간 정보, 도메인 지식(domain knowledge) 또는 인과적 모호성을 감소시킬 수 있는 다른 제약에 의존한다.

궁극적으로 인과 딥러닝(Causal Deep Learning)은 딥 신경망을 강력한 패턴 인식 시스템(pattern recognition system)에서 메커니즘과 결과를 추론할 수 있는 모델로 발전시키는 것을 목표로 한다. 신경 표현 학습을 구조적 인과성(structural causality), 개입, 불변성 및 반사실적 추론과 결합함으로써 익숙한 데이터를 넘어 일반화하고, 결과를 설명하며, 행동의 결과를 예측하고, 변화하는 환경에서도 강건한 의사결정(robust decision making)을 지원하는 인공지능 시스템으로 발전할 수 있는 경로를 제공한다.

##  

## 05.03. Causal Reinforcement Learning

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal reinforcement learning combines reinforcement learning with causal reasoning so that an agent can learn not only which actions produce high reward, but also why particular actions change the environment. Standard reinforcement learning often discovers effective policies through repeated interaction, yet the learned policy may depend heavily on correlations encountered during training. Causal reinforcement learning seeks policies grounded in intervention, mechanism, and structured environmental understanding.

The connection between reinforcement learning and causality is natural because actions are themselves interventions. When an agent selects an action, it deliberately changes part of the environment and observes the resulting transition. This differs from passive prediction, where the model only estimates relationships among observed variables. By treating actions as interventions, causal reinforcement learning can distinguish effects produced by the agent from changes caused by external processes or hidden environmental factors.

A Markov Decision Process provides the conventional foundation for reinforcement learning through states, actions, transition probabilities, rewards, and policies. Causal reinforcement learning extends this view by representing the transition process using causal variables and mechanisms. Instead of modeling only the probability of the next state, the agent may represent how specific components of the current state and chosen action cause particular components of the future state.

Structural causal models can therefore be integrated with reinforcement learning environments. State variables become nodes in a causal graph, actions can intervene on selected mechanisms, and transition dynamics are represented through structural equations. Such models allow the agent to reason about which variables directly influence others and which relationships remain unchanged when particular interventions or environmental conditions vary.

This structure supports more efficient exploration. In ordinary reinforcement learning, the agent may need many trials to discover which actions matter because it treats the environment largely as a black box. A causal model can identify variables that are likely to influence desired outcomes and direct exploration toward informative interventions. The agent can therefore reduce unnecessary experiments while learning more about the mechanisms that determine reward and state transitions.

Causal exploration is particularly valuable when interaction is expensive or dangerous. Robots, autonomous vehicles, industrial systems, and healthcare decision systems cannot freely test arbitrary actions in the real world. If an agent can infer causal relationships from previous experience, demonstrations, simulations, or limited interventions, it can prioritize safer and more informative actions rather than relying on unrestricted trial and error.

Counterfactual reasoning provides another important capability. After observing the result of an action, the agent can ask what might have happened if a different action had been chosen under the same background conditions. A causal model can estimate alternative trajectories without physically executing every candidate action. These counterfactual estimates can improve policy evaluation, credit assignment, and decision making when direct experimentation is limited.

Credit assignment is a central reinforcement learning problem because a delayed reward may result from a long sequence of actions. Causal structure can help identify which actions and intermediate variables actually contributed to the outcome. Instead of assigning influence primarily through temporal proximity, the agent can use causal dependencies to determine which decisions changed the mechanisms responsible for later rewards.

Causal reinforcement learning can also improve robustness under distribution shift. A conventional policy may exploit correlations that hold only in the training environment. When object appearances, background conditions, sensor characteristics, traffic patterns, or task configurations change, these correlations may fail. Policies based on stable causal mechanisms have a better chance of transferring because they depend on relationships governing how actions produce consequences.

Multiple environments provide useful information for learning such stable mechanisms. If some correlations change across environments while action-effect relationships remain consistent, the agent can identify which parts of its internal model are invariant. This can support policy transfer from simulation to reality, from one robot platform to another, or from one operational environment to another without relearning the complete policy from the beginning.

Causal state representation is therefore important. High-dimensional observations such as images, LiDAR, language, and proprioceptive signals may contain many details that do not directly affect decision making. An encoder can transform these observations into latent causal states representing objects, positions, contacts, forces, goals, hazards, or other meaningful variables. Reinforcement learning can then operate on a representation closer to the underlying mechanisms of the environment.

Model-based reinforcement learning is especially compatible with this approach. A learned world model predicts future states and rewards from current states and actions. When the world model includes causal structure, actions can be treated explicitly as interventions and future trajectories can be generated according to learned mechanisms. Planning algorithms can then compare candidate action sequences through internal simulation before selecting an action for execution.

This differs from purely predictive world modeling because causal structure attempts to describe how changes propagate. A model might predict that an object will move because similar trajectories appeared in training data, while a causal world model represents that applying force through contact changes velocity and position. Such mechanistic structure can make predictions more reliable when the agent encounters combinations of states and actions not frequently observed during training.

Offline reinforcement learning can also benefit from causal reasoning. Offline agents learn from previously collected datasets without unrestricted interaction with the environment. These datasets may contain strong selection bias because actions were generated by particular historical policies. Causal methods can help distinguish the effect of an action from the circumstances under which that action happened to be selected, improving policy evaluation and reducing misleading conclusions from observational data.

Confounding is especially relevant in these settings. A hidden or observed variable may influence both the selected action and the resulting reward, making the action appear more effective or harmful than it truly is. Causal reinforcement learning attempts to identify, adjust for, or otherwise model such confounding factors so that estimated action effects more accurately represent what would happen under deliberate policy intervention.

Hierarchical reinforcement learning can also be connected to causal mechanisms. Complex tasks may be decomposed into relatively independent subgoals and reusable skills. If these modules correspond to causal mechanisms, an agent can transfer individual skills when only part of the environment changes. This modularity can reduce relearning and support compositional behavior in tasks where familiar mechanisms appear in new combinations.

Multi-agent reinforcement learning introduces further causal complexity because each agent's action can influence the observations and decisions of other agents. A causal model can represent direct and indirect interactions among agents and help distinguish coordination effects from common environmental causes. This can support reasoning about cooperation, competition, communication, and responsibility in systems where many decision makers interact simultaneously.

For robotics, causal reinforcement learning is particularly attractive because embodied agents naturally generate intervention data. A robot can push, grasp, rotate, accelerate, stop, open, or manipulate objects and directly observe how the environment responds. These interactions reveal action-effect relationships that are difficult to infer from passive visual observation alone and can gradually build a structured model of physical affordances and dynamics.

A mobile robot, for example, can learn that steering changes heading, acceleration changes velocity, obstacles constrain motion, and surface properties influence traction. A manipulation robot can learn how grasp pose, applied force, object geometry, and contact conditions affect object motion. Encoding these relationships causally can improve planning when the robot faces unfamiliar objects, altered payloads, or new environmental conditions.

Safety is another important motivation. Reinforcement learning policies optimized only for expected reward may exploit unintended shortcuts or unsafe behaviors that happen to receive favorable training signals. A causal model can represent how actions influence hazards, constraints, and safety-critical variables. Planning can then reject interventions likely to produce dangerous downstream consequences even when such actions appear attractive according to short-term reward.

Causal reasoning can also support explanation of agent decisions. Instead of reporting only that a policy selected a particular action, the system can identify which state variables influenced the decision and what outcomes were expected to change as a result. Such explanations are valuable in autonomous systems, industrial control, healthcare, and other applications where operators need to understand the mechanisms behind an AI-generated decision.

Evaluation should therefore examine more than cumulative reward in familiar environments. Causal reinforcement learning systems can be tested on intervention prediction, counterfactual accuracy, transfer to changed environments, robustness to confounding, sample efficiency, and adaptation after mechanism changes. A strong causal agent should preserve useful knowledge when irrelevant correlations change and update only those components associated with genuinely altered mechanisms.

Important limitations remain because causal structure cannot automatically be recovered from arbitrary interaction data. Hidden confounders, insufficient exploration, partial observability, incorrect structural assumptions, and limited intervention diversity can all produce inaccurate causal models. The agent must therefore combine environmental interaction with suitable inductive biases, temporal information, domain knowledge, multimodal observations, or experimental design strategies.

Causal reinforcement learning ultimately aims to move reinforcement learning from trial-and-error policy optimization toward mechanism-aware decision making. By interpreting actions as interventions and combining causal representations, structural models, counterfactual reasoning, and policy learning, it provides a pathway toward agents that explore more efficiently, transfer knowledge more reliably, reason about consequences, and act more safely in changing real-world environments.

인과 강화학습(Causal Reinforcement Learning)은 강화학습(reinforcement learning)과 인과 추론(causal reasoning)을 결합하여 에이전트(agent)가 어떤 행동이 높은 보상(reward)을 만들어내는지만 학습하는 것이 아니라, 특정 행동이 왜 환경을 변화시키는지도 학습하도록 한다. 일반적인 강화학습은 반복적인 상호작용을 통해 효과적인 정책(policy)을 발견할 수 있지만, 학습된 정책이 훈련 과정에서 나타난 상관관계에 크게 의존할 수 있다. 인과 강화학습은 개입(intervention), 메커니즘(mechanism), 구조화된 환경 이해(structured environmental understanding)에 기반한 정책을 학습하는 것을 목표로 한다.

강화학습과 인과성(causality)의 연결은 행동(action) 자체가 개입이기 때문에 자연스럽다. 에이전트가 행동을 선택하면 환경의 일부를 의도적으로 변화시키고 그 결과로 발생하는 상태 전이(transition)를 관측한다. 이는 모델이 관측 변수들 사이의 관계만 추정하는 수동적 예측(passive prediction)과 다르다. 행동을 개입으로 취급하면 인과 강화학습은 에이전트가 만들어낸 효과와 외부 과정 또는 숨겨진 환경 요인에 의해 발생한 변화를 구별할 수 있다.

마르코프 의사결정 과정(Markov Decision Process, MDP)은 상태(state), 행동(action), 전이 확률(transition probability), 보상(reward), 정책(policy)을 통해 강화학습의 전통적인 기반을 제공한다. 인과 강화학습은 전이 과정을 인과 변수(causal variable)와 메커니즘으로 표현함으로써 이러한 관점을 확장한다. 단순히 다음 상태의 확률을 모델링하는 대신, 현재 상태의 특정 구성 요소와 선택된 행동이 미래 상태의 특정 구성 요소를 어떻게 발생시키는지를 표현할 수 있다.

따라서 구조적 인과 모델(Structural Causal Model, SCM)을 강화학습 환경과 통합할 수 있다. 상태 변수는 인과 그래프(causal graph)의 노드(node)가 되고, 행동은 선택된 메커니즘에 개입할 수 있으며, 전이 동역학(transition dynamics)은 구조 방정식(structural equation)을 통해 표현된다. 이러한 모델을 사용하면 에이전트는 어떤 변수가 다른 변수에 직접 영향을 주는지, 그리고 특정 개입이나 환경 조건이 달라질 때 어떤 관계가 그대로 유지되는지를 추론할 수 있다.

이러한 구조는 더욱 효율적인 탐색(exploration)을 지원한다. 일반적인 강화학습에서는 환경을 상당 부분 블랙박스(black box)로 취급하기 때문에 어떤 행동이 중요한지를 발견하려면 많은 시행이 필요할 수 있다. 인과 모델은 원하는 결과에 영향을 줄 가능성이 높은 변수를 식별하고 탐색을 정보 가치가 높은 개입으로 유도할 수 있다. 따라서 에이전트는 불필요한 실험을 줄이면서 보상과 상태 전이를 결정하는 메커니즘을 더욱 효과적으로 학습할 수 있다.

인과 탐색(causal exploration)은 상호작용 비용이 높거나 위험한 환경에서 특히 중요하다. 로봇, 자율주행차, 산업 시스템, 의료 의사결정 시스템은 실제 환경에서 임의의 행동을 자유롭게 시험할 수 없다. 에이전트가 이전 경험, 시연(demonstration), 시뮬레이션(simulation), 제한된 개입으로부터 인과관계를 추론할 수 있다면 제한 없는 시행착오에 의존하지 않고 더욱 안전하면서도 정보 가치가 높은 행동을 우선적으로 선택할 수 있다.

반사실적 추론(counterfactual reasoning)은 또 하나의 중요한 능력을 제공한다. 어떤 행동의 결과를 관측한 후 에이전트는 동일한 배경 조건에서 다른 행동을 선택했다면 어떤 일이 발생했을지를 질문할 수 있다. 인과 모델은 모든 후보 행동을 물리적으로 실행하지 않고도 대안적인 궤적(alternative trajectory)을 추정할 수 있다. 이러한 반사실적 추정(counterfactual estimation)은 직접적인 실험이 제한될 때 정책 평가(policy evaluation), 공헌도 할당(credit assignment), 의사결정을 향상시킬 수 있다.

공헌도 할당(credit assignment)은 지연된 보상(delayed reward)이 긴 행동 시퀀스의 결과로 발생할 수 있기 때문에 강화학습의 핵심적인 문제이다. 인과 구조는 어떤 행동과 중간 변수가 실제로 결과에 기여했는지를 식별하는 데 도움을 줄 수 있다. 단순히 시간적으로 가까운 행동에 영향력을 할당하는 대신, 에이전트는 인과 의존관계(causal dependency)를 사용하여 이후 보상을 발생시키는 메커니즘을 실제로 변화시킨 의사결정이 무엇인지 판단할 수 있다.

인과 강화학습은 분포 변화(distribution shift)에 대한 강건성(robustness)도 향상시킬 수 있다. 일반적인 정책은 훈련 환경에서만 성립하는 상관관계를 이용할 수 있다. 객체의 외형, 배경 조건, 센서 특성, 교통 패턴 또는 작업 구성이 변화하면 이러한 상관관계는 실패할 수 있다. 안정적인 인과 메커니즘에 기반한 정책은 행동이 결과를 만들어내는 관계에 의존하기 때문에 새로운 환경으로 전이될 가능성이 더 높다.

다중 환경(multiple environments)은 이러한 안정적인 메커니즘을 학습하는 데 유용한 정보를 제공한다. 환경에 따라 일부 상관관계가 달라지지만 행동과 결과의 관계가 일관되게 유지된다면 에이전트는 내부 모델에서 어떤 부분이 불변(invariant)인지를 식별할 수 있다. 이를 통해 전체 정책을 처음부터 다시 학습하지 않고 시뮬레이션에서 현실로, 하나의 로봇 플랫폼에서 다른 플랫폼으로, 또는 하나의 운영 환경에서 다른 환경으로 정책을 전이할 수 있다.

따라서 인과 상태 표현(causal state representation)이 중요하다. 이미지, 라이다(LiDAR), 언어, 고유수용감각(proprioceptive signal)과 같은 고차원 관측에는 의사결정에 직접 영향을 주지 않는 많은 세부 정보가 포함될 수 있다. 인코더(encoder)는 이러한 관측을 객체, 위치, 접촉, 힘, 목표, 위험 요소 또는 기타 의미 있는 변수를 나타내는 잠재 인과 상태(latent causal state)로 변환할 수 있다. 강화학습은 이후 환경의 근본적인 메커니즘에 더 가까운 표현을 기반으로 동작할 수 있다.

모델 기반 강화학습(model-based reinforcement learning)은 이러한 접근법과 특히 잘 결합된다. 학습된 월드 모델(world model)은 현재 상태와 행동으로부터 미래 상태와 보상을 예측한다. 월드 모델에 인과 구조가 포함되면 행동을 명시적인 개입으로 취급하고 학습된 메커니즘에 따라 미래 궤적을 생성할 수 있다. 계획 알고리즘(planning algorithm)은 실제 행동을 실행하기 전에 내부 시뮬레이션을 통해 여러 후보 행동 시퀀스를 비교할 수 있다.

이는 인과 구조가 변화가 어떻게 전파되는지를 설명하려 한다는 점에서 순수한 예측 기반 월드 모델링(predictive world modeling)과 다르다. 모델은 훈련 데이터에서 비슷한 궤적을 관측했다는 이유만으로 물체가 움직일 것이라고 예측할 수도 있지만, 인과 월드 모델(causal world model)은 접촉을 통해 힘을 가하면 속도와 위치가 변화한다는 관계를 표현한다. 이러한 메커니즘 구조는 훈련 과정에서 자주 관측되지 않은 상태와 행동의 조합을 만났을 때 더욱 신뢰성 있는 예측을 가능하게 할 수 있다.

오프라인 강화학습(offline reinforcement learning) 역시 인과 추론의 혜택을 받을 수 있다. 오프라인 에이전트는 환경과 자유롭게 상호작용하지 않고 이전에 수집된 데이터셋으로부터 학습한다. 이러한 데이터셋은 특정 과거 정책에 의해 행동이 생성되었기 때문에 강한 선택 편향(selection bias)을 포함할 수 있다. 인과 방법은 행동 자체의 효과와 해당 행동이 선택되었던 상황을 구분하여 정책 평가를 개선하고 관측 데이터로부터 잘못된 결론을 도출할 가능성을 줄일 수 있다.

교란(confounding)은 이러한 환경에서 특히 중요하다. 숨겨진 변수 또는 관측 가능한 변수가 선택된 행동과 결과 보상 모두에 영향을 주면 해당 행동이 실제보다 더 효과적이거나 더 해로운 것처럼 보일 수 있다. 인과 강화학습은 이러한 교란 요인(confounding factor)을 식별하거나 조정하거나 모델링하여 추정된 행동 효과가 의도적인 정책 개입(policy intervention)을 수행했을 때 실제로 발생할 결과를 더욱 정확하게 나타내도록 한다.

계층적 강화학습(hierarchical reinforcement learning) 역시 인과 메커니즘과 연결될 수 있다. 복잡한 작업은 비교적 독립적인 하위 목표(subgoal)와 재사용 가능한 기술(skill)로 분해될 수 있다. 이러한 모듈이 인과 메커니즘과 대응한다면 환경의 일부만 변화했을 때 개별 기술을 다른 상황으로 전이할 수 있다. 이러한 모듈성(modularity)은 재학습을 줄이고 익숙한 메커니즘이 새로운 조합으로 등장하는 작업에서 조합적 행동(compositional behavior)을 지원할 수 있다.

다중 에이전트 강화학습(multi-agent reinforcement learning)은 각 에이전트의 행동이 다른 에이전트의 관측과 의사결정에 영향을 줄 수 있기 때문에 추가적인 인과적 복잡성을 갖는다. 인과 모델은 에이전트 사이의 직접적·간접적 상호작용을 표현하고 협력 효과와 공통 환경 원인(common environmental cause)을 구별하는 데 도움을 줄 수 있다. 이를 통해 여러 의사결정 주체가 동시에 상호작용하는 시스템에서 협력, 경쟁, 통신 및 책임에 대한 추론을 지원할 수 있다.

로보틱스(robotics)에서는 체화된 에이전트(embodied agent)가 자연스럽게 개입 데이터를 생성하기 때문에 인과 강화학습이 특히 매력적이다. 로봇은 물체를 밀고, 잡고, 회전시키고, 가속하고, 정지하고, 열거나 조작하면서 환경이 어떻게 반응하는지를 직접 관측할 수 있다. 이러한 상호작용은 수동적인 시각 관측만으로 추론하기 어려운 행동-결과 관계(action-effect relationship)를 드러내며 물리적 행동유도성(affordance)과 동역학에 관한 구조화된 모델을 점진적으로 구축할 수 있게 한다.

예를 들어 이동 로봇(mobile robot)은 조향이 방향을 변화시키고, 가속이 속도를 변화시키며, 장애물이 이동을 제한하고, 노면 특성이 접지력(traction)에 영향을 준다는 관계를 학습할 수 있다. 조작 로봇(manipulation robot)은 파지 자세(grasp pose), 적용된 힘, 객체 형상, 접촉 조건이 물체 운동에 어떤 영향을 주는지 학습할 수 있다. 이러한 관계를 인과적으로 부호화하면 낯선 객체, 변경된 페이로드(payload), 새로운 환경 조건에서도 계획 성능을 향상시킬 수 있다.

안전성(safety)은 또 다른 중요한 동기이다. 기대 보상(expected reward)만을 최적화하는 강화학습 정책은 의도하지 않은 지름길이나 훈련 신호에서 유리한 보상을 받는 위험한 행동을 이용할 수 있다. 인과 모델은 행동이 위험 요소, 제약 조건 및 안전 중요 변수(safety-critical variable)에 어떤 영향을 미치는지를 표현할 수 있다. 계획 시스템은 단기 보상 측면에서 매력적으로 보이더라도 위험한 후속 결과를 발생시킬 가능성이 높은 개입을 배제할 수 있다.

인과 추론은 에이전트의 의사결정에 대한 설명(explanation)도 지원할 수 있다. 단순히 정책이 특정 행동을 선택했다고 보고하는 대신 어떤 상태 변수가 의사결정에 영향을 주었으며, 해당 행동의 결과로 어떤 결과가 변화할 것으로 예상되었는지를 식별할 수 있다. 이러한 설명은 운영자가 인공지능이 생성한 의사결정의 기반 메커니즘을 이해해야 하는 자율 시스템, 산업 제어, 의료 및 기타 응용 분야에서 중요하다.

따라서 평가(evaluation)는 익숙한 환경에서의 누적 보상(cumulative reward)만을 측정해서는 안 된다. 인과 강화학습 시스템은 개입 예측(intervention prediction), 반사실적 정확도(counterfactual accuracy), 변화된 환경으로의 전이, 교란에 대한 강건성, 샘플 효율성(sample efficiency), 메커니즘 변화 이후의 적응 능력 등을 평가할 수 있다. 강력한 인과 에이전트는 관련 없는 상관관계가 변화하더라도 유용한 지식을 유지하고 실제로 변경된 메커니즘과 관련된 구성 요소만 갱신할 수 있어야 한다.

그러나 인과 구조를 임의의 상호작용 데이터로부터 자동으로 복원할 수 없다는 중요한 한계가 남아 있다. 숨겨진 교란 요인(hidden confounder), 불충분한 탐색, 부분 관측 가능성(partial observability), 잘못된 구조적 가정, 제한된 개입 다양성은 모두 부정확한 인과 모델을 만들 수 있다. 따라서 에이전트는 환경과의 상호작용을 적절한 귀납적 편향(inductive bias), 시간 정보, 도메인 지식(domain knowledge), 다중 모달 관측(multimodal observation), 또는 실험 설계(experimental design) 전략과 결합해야 한다.

궁극적으로 인과 강화학습(Causal Reinforcement Learning)은 강화학습을 단순한 시행착오 기반 정책 최적화(trial-and-error policy optimization)에서 메커니즘 인식 의사결정(mechanism-aware decision making)으로 발전시키는 것을 목표로 한다. 행동을 개입으로 해석하고 인과 표현(causal representation), 구조적 모델(structural model), 반사실적 추론 및 정책 학습을 결합함으로써 더욱 효율적으로 탐색하고, 지식을 더욱 안정적으로 전이하며, 행동의 결과를 추론하고, 변화하는 실제 환경에서 더욱 안전하게 행동할 수 있는 에이전트로 발전하는 경로를 제공한다.

##  

## 05.04. Causal LLMs

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal LLMs combine the language understanding and generation capabilities of large language models with explicit ideas from causal inference and structural causal reasoning. Conventional LLMs learn statistical dependencies among tokens, concepts, events, and descriptions from large text corpora. Causal LLMs aim to move beyond association by representing why events occur, how interventions change outcomes, and which mechanisms remain stable across changing contexts.

An important challenge is that natural language contains enormous amounts of causal information, but most of it is expressed indirectly. Text describes actions, consequences, explanations, experiments, failures, intentions, and hypothetical alternatives without providing explicit causal graphs. A causal LLM must therefore distinguish statements of correlation from claims of causation and infer candidate relationships while preserving uncertainty about relationships that are not sufficiently supported.

Structural causal models provide one possible framework for organizing this information. Entities, events, conditions, and outcomes can be mapped to causal variables, while directed relationships describe how one variable influences another. An LLM can help identify candidate variables and mechanisms from unstructured text, while a structured causal component constrains reasoning about interventions, dependencies, confounders, mediators, and downstream effects.

This creates an important distinction between linguistic prediction and causal reasoning. Predicting that two events commonly appear together in text does not establish that one causes the other. A language model may reproduce frequent explanations from its training data even when those explanations reflect bias or convention. Causal reasoning requires asking whether changing a proposed cause would change the outcome while other relevant conditions are appropriately controlled.

Intervention-based reasoning allows an LLM to answer questions that go beyond ordinary conditional prediction. Instead of asking what normally follows a particular situation, the system can reason about what would happen if a variable were deliberately changed. Connecting language representations with the do-operator or an intervention model enables the system to distinguish observed evidence from hypothetical manipulation and to trace how effects may propagate through a causal structure.

Counterfactual reasoning extends this capability to alternative histories. After representing an observed event and its background conditions, a causal LLM can consider what might have happened if one decision, action, treatment, or environmental condition had been different. This supports explanations, decision analysis, debugging, policy reasoning, scientific investigation, and planning where users need to compare actual outcomes with plausible alternatives.

Causal knowledge graphs can provide an external structure for this reasoning. An LLM may extract entities and relations from documents and organize them into graphs representing causes, effects, mechanisms, evidence, and contextual conditions. Retrieval can then supply relevant causal structures during inference, allowing the model to reason with explicit relationships rather than relying only on causal patterns implicitly stored in neural parameters.

Tool use is also important because reliable causal analysis often requires capabilities beyond text generation. A causal LLM can interact with statistical packages, causal discovery algorithms, simulation environments, databases, experiment records, or structural models. The LLM can interpret the user\'s problem and formulate hypotheses, while specialized tools estimate effects, test assumptions, simulate interventions, or evaluate alternative causal structures.

Scientific applications are particularly suitable because scientific reasoning frequently involves hypotheses about mechanisms and experimental interventions. A causal LLM can connect published knowledge, experimental observations, equations, and domain constraints to propose candidate explanations. It can then help formulate experiments that distinguish competing hypotheses, making the language model part of an iterative cycle of hypothesis generation, intervention, observation, and model revision.

Causal LLMs can also improve decision-support systems. In medicine, engineering, economics, and operations, users often ask not merely what is likely to happen but what action could change the outcome. A causally structured system can separate risk factors from actionable causes, identify potential confounders, compare interventions, and explain which assumptions influence a recommendation rather than presenting predictive correlations as direct prescriptions.

For robotics and embodied AI, an LLM can connect language-level reasoning with a causal world model. Instructions such as moving an object, avoiding a hazard, or repairing a failure can be translated into candidate interventions on a structured representation of the environment. The world model predicts how those interventions affect future states, while the LLM interprets goals, constraints, explanations, and high-level plans expressed in language.

Causal reasoning may also contribute to reducing some forms of hallucination, although it does not automatically guarantee factual correctness. A model constrained to maintain consistent causal relationships can detect contradictions between proposed causes and expected effects. External evidence, retrieval, tools, and structured models remain necessary because an internally coherent causal explanation can still be based on incorrect assumptions or incomplete information.

Evaluation therefore requires more than conventional language benchmarks. A causal LLM should be tested on causal direction, confounding, intervention prediction, counterfactual reasoning, mechanism transfer, and robustness when superficial correlations change. Evaluation should also examine whether explanations correspond to the model\'s actual causal assumptions and whether answers change appropriately when relevant variables or background conditions are modified.

Ultimately, Causal LLMs represent a bridge between statistical language modeling and mechanism-based reasoning. Their objective is not to replace the generative capabilities of LLMs, but to complement them with explicit representations of causes, interventions, counterfactuals, and stable mechanisms. Such integration can support more reliable reasoning, scientific discovery, planning, explanation, and decision making as language models become components of increasingly autonomous AI systems.

인과 대규모 언어 모델(Causal LLMs)은 대규모 언어 모델(Large Language Model, LLM)의 언어 이해 및 생성 능력과 인과 추론(causal inference), 구조적 인과 추론(structural causal reasoning)의 명시적인 개념을 결합한다. 기존 LLM은 대규모 텍스트 말뭉치(text corpus)에서 토큰(token), 개념, 사건, 설명 사이의 통계적 의존관계(statistical dependency)를 학습한다. 인과 LLM은 이러한 연관성을 넘어 사건이 왜 발생하는지, 개입(intervention)이 결과를 어떻게 변화시키는지, 그리고 변화하는 맥락에서도 어떤 메커니즘이 안정적으로 유지되는지를 표현하는 것을 목표로 한다.

중요한 과제는 자연어(natural language)에 방대한 양의 인과 정보가 포함되어 있지만, 대부분이 간접적으로 표현된다는 점이다. 텍스트는 행동, 결과, 설명, 실험, 실패, 의도 및 가상적인 대안에 대해 기술하지만 명시적인 인과 그래프(causal graph)를 제공하는 경우는 드물다. 따라서 인과 LLM은 상관관계에 관한 진술과 인과관계에 관한 주장을 구별하고, 충분히 뒷받침되지 않은 관계에 대해서는 불확실성을 유지하면서 후보 인과관계를 추론해야 한다.

구조적 인과 모델(Structural Causal Model, SCM)은 이러한 정보를 구성하는 하나의 가능한 프레임워크를 제공한다. 개체(entity), 사건(event), 조건(condition), 결과(outcome)를 인과 변수(causal variable)에 대응시키고, 방향성 관계(directed relationship)를 통해 하나의 변수가 다른 변수에 어떻게 영향을 미치는지를 표현할 수 있다. LLM은 비정형 텍스트(unstructured text)에서 후보 변수와 메커니즘을 식별하고, 구조화된 인과 구성 요소는 개입, 의존관계, 교란 요인(confounder), 매개 변수(mediator), 후속 효과(downstream effect)에 관한 추론을 제약할 수 있다.

이는 언어적 예측(linguistic prediction)과 인과 추론(causal reasoning) 사이에 중요한 차이를 만든다. 두 사건이 텍스트에서 자주 함께 등장할 것이라고 예측하는 것만으로는 하나가 다른 하나의 원인이라는 사실을 확립할 수 없다. 언어 모델은 그러한 설명이 편향(bias)이나 관습을 반영하더라도 훈련 데이터에서 자주 등장한 설명을 재생산할 수 있다. 인과 추론은 관련된 다른 조건들을 적절하게 통제하면서 제안된 원인을 변화시켰을 때 결과도 변화하는지를 질문해야 한다.

개입 기반 추론(intervention-based reasoning)을 사용하면 LLM은 일반적인 조건부 예측(conditional prediction)을 넘어서는 질문에 답할 수 있다. 특정 상황에서 일반적으로 무엇이 뒤따르는지를 묻는 대신, 어떤 변수를 의도적으로 변경했을 때 무엇이 발생할지를 추론할 수 있다. 언어 표현(language representation)을 두 연산자(do-operator) 또는 개입 모델(intervention model)과 연결하면 관측된 증거와 가상의 조작을 구별하고, 인과 구조를 통해 효과가 어떻게 전파되는지를 추적할 수 있다.

반사실적 추론(counterfactual reasoning)은 이러한 능력을 대안적 역사(alternative history)에 대한 추론으로 확장한다. 관측된 사건과 그 배경 조건을 표현한 후, 인과 LLM은 하나의 의사결정, 행동, 처치 또는 환경 조건이 달랐다면 어떤 일이 발생했을지를 고려할 수 있다. 이를 통해 사용자가 실제 결과와 가능한 대안을 비교해야 하는 설명, 의사결정 분석, 디버깅(debugging), 정책 추론(policy reasoning), 과학적 조사 및 계획(planning)을 지원할 수 있다.

인과 지식 그래프(causal knowledge graph)는 이러한 추론을 위한 외부 구조를 제공할 수 있다. LLM은 문서에서 개체와 관계를 추출하여 원인, 결과, 메커니즘, 증거 및 맥락 조건을 나타내는 그래프로 구성할 수 있다. 이후 검색(retrieval)을 통해 추론 과정에 관련된 인과 구조를 제공함으로써, 모델이 신경망 매개변수(neural parameter)에 암묵적으로 저장된 인과 패턴에만 의존하지 않고 명시적인 관계를 이용하여 추론하도록 만들 수 있다.

도구 사용(tool use) 역시 중요하다. 신뢰성 있는 인과 분석에는 텍스트 생성 이상의 능력이 필요한 경우가 많기 때문이다. 인과 LLM은 통계 패키지(statistical package), 인과 발견 알고리즘(causal discovery algorithm), 시뮬레이션 환경(simulation environment), 데이터베이스(database), 실험 기록 또는 구조적 모델과 상호작용할 수 있다. LLM은 사용자의 문제를 해석하고 가설을 구성하며, 전문 도구는 효과를 추정하고 가정을 검증하며 개입을 시뮬레이션하거나 대안적인 인과 구조를 평가할 수 있다.

과학적 응용(scientific application)은 과학적 추론이 메커니즘에 대한 가설과 실험적 개입을 빈번하게 포함하기 때문에 특히 적합하다. 인과 LLM은 출판된 지식, 실험 관측, 방정식 및 도메인 제약(domain constraint)을 연결하여 후보 설명을 제안할 수 있다. 이후 서로 경쟁하는 가설을 구별할 수 있는 실험을 구성하는 데 도움을 줄 수 있으며, 이를 통해 언어 모델은 가설 생성(hypothesis generation), 개입, 관측, 모델 수정(model revision)이 반복되는 순환 과정의 일부가 될 수 있다.

인과 LLM은 의사결정 지원 시스템(decision-support system)을 향상시키는 데에도 활용될 수 있다. 의료, 공학, 경제학 및 운영 분야에서 사용자는 단순히 어떤 일이 발생할 가능성이 높은지를 묻는 것이 아니라 어떤 행동이 결과를 변화시킬 수 있는지를 질문하는 경우가 많다. 인과적으로 구조화된 시스템은 위험 요인(risk factor)과 실제로 조작 가능한 원인(actionable cause)을 구별하고, 잠재적인 교란 요인을 식별하며, 여러 개입을 비교하고, 어떤 가정이 권고에 영향을 미치는지를 설명함으로써 예측적 상관관계를 직접적인 처방으로 잘못 제시하는 것을 줄일 수 있다.

로보틱스(robotics)와 체화 인공지능(embodied AI)에서는 LLM이 언어 수준의 추론(language-level reasoning)을 인과 월드 모델(causal world model)과 연결할 수 있다. 물체 이동, 위험 회피, 고장 복구와 같은 지시는 환경의 구조화된 표현에 적용되는 후보 개입(candidate intervention)으로 변환될 수 있다. 월드 모델은 이러한 개입이 미래 상태에 어떤 영향을 미치는지를 예측하고, LLM은 언어로 표현된 목표, 제약 조건, 설명 및 상위 수준 계획(high-level plan)을 해석할 수 있다.

인과 추론은 일부 형태의 환각(hallucination)을 줄이는 데에도 기여할 가능성이 있지만, 이것이 자동으로 사실적 정확성(factual correctness)을 보장하는 것은 아니다. 일관된 인과관계를 유지하도록 제약된 모델은 제안된 원인과 예상되는 결과 사이의 모순을 탐지할 수 있다. 그러나 내부적으로 일관된 인과 설명이라도 잘못된 가정이나 불완전한 정보에 기반할 수 있으므로 외부 증거(external evidence), 검색, 도구 및 구조화된 모델이 여전히 필요하다.

따라서 평가(evaluation)에는 기존의 언어 벤치마크(language benchmark) 이상의 기준이 필요하다. 인과 LLM은 인과 방향(causal direction), 교란(confounding), 개입 예측(intervention prediction), 반사실적 추론, 메커니즘 전이(mechanism transfer), 표면적인 상관관계가 변화했을 때의 강건성(robustness) 등을 평가해야 한다. 또한 설명이 모델의 실제 인과적 가정과 대응하는지, 관련 변수나 배경 조건을 변경했을 때 답변이 적절하게 변화하는지도 평가해야 한다.

궁극적으로 인과 대규모 언어 모델(Causal LLMs)은 통계적 언어 모델링(statistical language modeling)과 메커니즘 기반 추론(mechanism-based reasoning)을 연결하는 다리라고 할 수 있다. 그 목적은 LLM의 생성 능력을 대체하는 것이 아니라 원인, 개입, 반사실(counterfactual), 안정적인 메커니즘에 대한 명시적 표현으로 이를 보완하는 것이다. 이러한 통합은 언어 모델이 점점 더 자율적인 인공지능 시스템의 구성 요소가 되어가는 과정에서 더욱 신뢰성 있는 추론, 과학적 발견, 계획, 설명 및 의사결정을 지원할 수 있다.

##  

## 05.05. Causal Generalization

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal generalization refers to the ability of an AI system to preserve useful knowledge when the statistical distribution of observations changes but the underlying causal mechanisms remain stable. Conventional machine learning often generalizes by interpolating within patterns similar to the training data, whereas causal generalization seeks relationships that continue to hold across environments, domains, interventions, and previously unseen combinations of conditions.

The central idea is that correlations may vary while causal mechanisms remain comparatively invariant. A feature that predicts an outcome in one dataset may lose its predictive value when background conditions change, especially when the feature is only indirectly associated with the outcome. By identifying variables that directly participate in stable mechanisms, a causal model can reduce dependence on spurious correlations and improve out-of-distribution generalization.

This distinction can be expressed through changes in data-generating processes. Different environments may alter the distributions of inputs, confounders, or contextual variables while leaving selected structural relationships unchanged. Causal generalization attempts to discover which parts of the system are invariant and which are environment-specific, allowing a model to reuse stable mechanisms rather than relearning every relationship whenever the operational context changes.

Invariant causal prediction provides an important conceptual foundation for this approach. If a set of variables represents genuine causes of a target under suitable assumptions, the conditional relationship between those causes and the target should remain stable across environments where unrelated mechanisms change. Learning algorithms can therefore compare multiple environments and prefer representations or predictors whose relationships remain consistent despite changing observational distributions.

Causal representation learning contributes by transforming high-dimensional observations into latent variables that correspond more closely to underlying mechanisms. Images, language, sensor measurements, and other complex inputs may contain numerous irrelevant details. A causally structured representation seeks to preserve variables such as object identity, physical state, action, force, context, or environmental condition while separating factors whose correlations are accidental or domain-specific.

Interventions provide stronger evidence for generalization because they reveal how systems respond when selected variables are deliberately changed. A model that has learned the effect of an intervention can often apply that mechanism in situations where surface appearances differ. Instead of asking only whether two variables usually occur together, causal generalization asks whether manipulating one variable produces a stable effect on another across relevant contexts.

Modularity is closely connected to this capability. Complex systems can often be decomposed into relatively independent causal mechanisms, each governing part of the overall process. When an environment changes, only a subset of these mechanisms may be affected. A modular causal model can update the changed component while preserving unaffected knowledge, making adaptation more efficient and reducing the risk of catastrophic changes to previously learned behavior.

Compositional generalization extends this principle to new combinations of familiar mechanisms. An AI system may encounter objects, actions, goals, or environmental conditions that were previously observed separately but never together. If its internal representation captures modular causal relationships, the system can combine known mechanisms to reason about novel situations rather than depending on memorized combinations from the training distribution.

Domain generalization and domain adaptation are related but not identical to causal generalization. Domain methods often seek representations that transfer across datasets or operational contexts, while causal generalization emphasizes why transfer should be possible. Stable causal mechanisms provide a structural explanation for invariance and can help determine which information should be retained, ignored, or adapted when moving between domains.

Causal generalization is particularly relevant to reinforcement learning and autonomous agents because actions continuously alter the environment. A policy trained only on correlations from one environment may fail when dynamics, sensors, objects, or task configurations change. If the agent represents how actions causally affect states and rewards, it can preserve useful action-effect knowledge and adapt more efficiently to new conditions.

World models provide a practical framework for implementing this capability. A causal world model represents states, actions, environmental variables, and transition mechanisms in a structured latent space. Planning can then simulate interventions under new conditions and reuse mechanisms learned elsewhere. When only one part of the environment changes, the model can revise that mechanism instead of discarding its complete predictive structure.

Robotics provides a clear example. A mobile robot may operate on different surfaces, under different lighting conditions, with altered payloads or sensor configurations. Visual appearance and measured dynamics may change, but fundamental relationships among steering, force, motion, collision, and object interaction can remain stable. Causal generalization seeks to preserve these relationships so that adaptation requires less data and fewer risky real-world trials.

Scientific AI also benefits because scientific laws are valuable precisely because they generalize beyond individual observations. A causal model that captures a mechanism can potentially transfer knowledge across experimental conditions, scales, or related systems. Combining learned representations with physical constraints, interventions, and structural assumptions can therefore support models that seek reusable explanations rather than dataset-specific predictive rules.

Evaluation of causal generalization should explicitly test environments that differ from training conditions. Useful criteria include performance under distribution shift, intervention prediction, mechanism transfer, compositional generalization, adaptation speed, and robustness when spurious correlations are deliberately modified. A model that performs well only on randomly held-out samples may still fail to demonstrate genuine causal generalization.

A major limitation is that invariant behavior does not automatically prove causality. Multiple predictors may remain stable across the environments included in training, while hidden confounders or unobserved mechanism changes may still produce incorrect conclusions. Reliable causal generalization therefore requires appropriate environmental diversity, structural assumptions, interventions, temporal information, domain knowledge, or experimental evidence that meaningfully constrains alternative explanations.

Ultimately, causal generalization aims to make AI systems reuse knowledge according to stable mechanisms rather than superficial similarity. It connects causal representation learning, causal deep learning, causal reinforcement learning, and causal LLMs by providing a common objective: discovering knowledge that survives environmental change. Such capability is central to robust AI systems expected to operate, reason, and adapt beyond the conditions represented in their original training data.

인과 일반화(Causal Generalization)는 관측 데이터의 통계적 분포(statistical distribution)가 변화하더라도 기반이 되는 인과 메커니즘(causal mechanism)이 안정적으로 유지될 때 인공지능 시스템이 유용한 지식을 보존하는 능력을 의미한다. 기존 머신러닝(conventional machine learning)은 주로 훈련 데이터와 유사한 패턴 안에서 보간(interpolation)함으로써 일반화하지만, 인과 일반화는 서로 다른 환경, 도메인, 개입(intervention), 그리고 이전에 경험하지 못한 조건의 조합에서도 유지되는 관계를 찾는 것을 목표로 한다.

핵심 개념은 상관관계(correlation)는 변화할 수 있지만 인과 메커니즘은 상대적으로 불변(invariant)할 수 있다는 것이다. 하나의 데이터셋에서 결과를 잘 예측하는 특징이라도 배경 조건이 변화하면 예측력이 사라질 수 있으며, 특히 해당 특징이 결과와 간접적으로만 연관되어 있을 때 이러한 문제가 발생한다. 안정적인 메커니즘에 직접 참여하는 변수를 식별하면 인과 모델(causal model)은 허위 상관관계(spurious correlation)에 대한 의존성을 줄이고 분포 외 일반화(out-of-distribution generalization)를 향상시킬 수 있다.

이러한 차이는 데이터 생성 과정(data-generating process)의 변화라는 관점에서 설명할 수 있다. 서로 다른 환경에서는 입력, 교란 요인(confounder), 맥락 변수(contextual variable)의 분포가 달라질 수 있지만 선택된 구조적 관계(structural relationship)는 그대로 유지될 수 있다. 인과 일반화는 시스템에서 어떤 부분이 불변이고 어떤 부분이 환경에 특화되어 있는지를 발견하여, 운영 맥락이 바뀔 때마다 모든 관계를 다시 학습하는 대신 안정적인 메커니즘을 재사용하도록 한다.

불변 인과 예측(Invariant Causal Prediction)은 이러한 접근법에 중요한 개념적 기반을 제공한다. 적절한 가정 아래에서 특정 변수 집합이 목표 변수의 실제 원인을 나타낸다면, 관련 없는 메커니즘이 변화하는 환경에서도 이러한 원인과 목표 사이의 조건부 관계(conditional relationship)는 안정적으로 유지되어야 한다. 따라서 학습 알고리즘은 여러 환경을 비교하여 관측 분포가 변화하더라도 일관된 관계를 유지하는 표현(representation)이나 예측기(predictor)를 선호할 수 있다.

인과 표현 학습(Causal Representation Learning)은 고차원 관측(high-dimensional observation)을 기반 메커니즘에 보다 직접적으로 대응하는 잠재 변수(latent variable)로 변환함으로써 이러한 과정에 기여한다. 이미지, 언어, 센서 측정 및 기타 복잡한 입력에는 수많은 관련 없는 세부 정보가 포함될 수 있다. 인과적으로 구조화된 표현은 객체 정체성(object identity), 물리적 상태(physical state), 행동(action), 힘(force), 맥락(context), 환경 조건과 같은 변수를 보존하면서 우연적이거나 도메인에 특화된 상관 요인을 분리하려 한다.

개입(intervention)은 선택된 변수를 의도적으로 변화시켰을 때 시스템이 어떻게 반응하는지를 보여주기 때문에 일반화에 더욱 강력한 증거를 제공한다. 개입의 효과를 학습한 모델은 표면적인 외형이 다른 상황에서도 동일한 메커니즘을 적용할 수 있다. 단순히 두 변수가 일반적으로 함께 나타나는지를 묻는 대신, 인과 일반화는 하나의 변수를 조작했을 때 다른 변수에 안정적인 효과가 발생하는지를 관련된 여러 맥락에서 확인한다.

모듈성(modularity)은 이러한 능력과 밀접하게 연결된다. 복잡한 시스템은 전체 과정의 일부를 담당하는 비교적 독립적인 여러 인과 메커니즘으로 분해할 수 있는 경우가 많다. 환경이 변화하면 이러한 메커니즘 가운데 일부만 영향을 받을 수 있다. 모듈형 인과 모델(modular causal model)은 영향을 받은 구성 요소만 갱신하면서 나머지 지식을 보존할 수 있으므로 적응(adaptation)을 더욱 효율적으로 수행하고 기존에 학습된 행동이 급격하게 손상될 위험을 줄일 수 있다.

조합적 일반화(compositional generalization)는 이러한 원리를 익숙한 메커니즘의 새로운 조합으로 확장한다. 인공지능 시스템은 이전에 각각 개별적으로 관측했지만 함께 경험한 적은 없는 객체, 행동, 목표 또는 환경 조건의 조합을 만날 수 있다. 내부 표현이 모듈화된 인과관계를 포착한다면 시스템은 훈련 분포에서 암기한 조합에 의존하지 않고 이미 알고 있는 메커니즘을 결합하여 새로운 상황을 추론할 수 있다.

도메인 일반화(domain generalization)와 도메인 적응(domain adaptation)은 인과 일반화와 관련되어 있지만 동일한 개념은 아니다. 도메인 방법은 일반적으로 서로 다른 데이터셋이나 운영 맥락 사이에서 전이 가능한 표현을 찾는 데 초점을 맞추지만, 인과 일반화는 왜 그러한 전이가 가능해야 하는지에 중점을 둔다. 안정적인 인과 메커니즘은 불변성에 대한 구조적 설명을 제공하며, 도메인 사이를 이동할 때 어떤 정보를 유지하고 무시하거나 적응시켜야 하는지를 결정하는 데 도움을 줄 수 있다.

인과 일반화는 행동이 지속적으로 환경을 변화시키는 강화학습(reinforcement learning)과 자율 에이전트(autonomous agent)에 특히 중요하다. 하나의 환경에서 나타난 상관관계만을 기반으로 학습된 정책(policy)은 동역학, 센서, 객체 또는 작업 구성이 변화하면 실패할 수 있다. 에이전트가 행동이 상태와 보상에 어떤 인과적 영향을 주는지를 표현한다면 유용한 행동-결과 지식(action-effect knowledge)을 보존하면서 새로운 조건에 더욱 효율적으로 적응할 수 있다.

월드 모델(world model)은 이러한 능력을 구현하기 위한 실용적인 프레임워크를 제공한다. 인과 월드 모델(causal world model)은 상태, 행동, 환경 변수 및 전이 메커니즘(transition mechanism)을 구조화된 잠재 공간(structured latent space)에 표현한다. 계획(planning) 과정에서는 새로운 조건에서 개입을 시뮬레이션하고 다른 환경에서 학습한 메커니즘을 재사용할 수 있다. 환경의 일부만 변화했다면 모델은 전체 예측 구조를 폐기하는 대신 해당 메커니즘만 수정할 수 있다.

로보틱스(robotics)는 이를 명확하게 보여주는 사례이다. 이동 로봇(mobile robot)은 서로 다른 노면, 조명 조건, 변경된 페이로드(payload), 또는 다른 센서 구성에서 동작할 수 있다. 시각적 외형과 측정된 동역학은 변화할 수 있지만 조향, 힘, 운동, 충돌, 객체 상호작용 사이의 기본적인 관계는 안정적으로 유지될 수 있다. 인과 일반화는 이러한 관계를 보존하여 더 적은 데이터와 더 적은 위험한 실제 환경 시험만으로 새로운 조건에 적응하도록 하는 것을 목표로 한다.

과학 인공지능(Scientific AI) 역시 과학 법칙이 개별적인 관측을 넘어 일반화될 수 있기 때문에 인과 일반화의 혜택을 받을 수 있다. 메커니즘을 포착한 인과 모델은 서로 다른 실험 조건, 규모 또는 관련 시스템 사이에서 지식을 전이할 가능성이 있다. 따라서 학습된 표현을 물리적 제약(physical constraint), 개입 및 구조적 가정(structural assumption)과 결합하면 데이터셋에 특화된 예측 규칙이 아니라 재사용 가능한 설명을 찾는 모델을 구축할 수 있다.

인과 일반화의 평가(evaluation)는 훈련 조건과 명확하게 다른 환경을 대상으로 수행되어야 한다. 유용한 평가 기준에는 분포 변화에서의 성능, 개입 예측(intervention prediction), 메커니즘 전이(mechanism transfer), 조합적 일반화, 적응 속도(adaptation speed), 그리고 허위 상관관계를 의도적으로 변경했을 때의 강건성(robustness)이 포함된다. 무작위로 분리된 테스트 샘플에서만 좋은 성능을 보이는 모델은 진정한 인과 일반화를 입증하지 못할 수 있다.

중요한 한계는 불변적인 행동이 자동으로 인과성을 증명하는 것은 아니라는 점이다. 여러 예측기가 훈련에 포함된 환경에서는 안정적으로 유지될 수 있지만, 숨겨진 교란 요인(hidden confounder)이나 관측되지 않은 메커니즘 변화로 인해 여전히 잘못된 결론이 만들어질 수 있다. 따라서 신뢰할 수 있는 인과 일반화를 위해서는 적절한 환경 다양성(environmental diversity), 구조적 가정, 개입, 시간 정보(temporal information), 도메인 지식(domain knowledge), 또는 대안적인 설명을 의미 있게 제한할 수 있는 실험적 증거가 필요하다.

궁극적으로 인과 일반화(Causal Generalization)는 인공지능 시스템이 표면적인 유사성(superficial similarity)이 아니라 안정적인 메커니즘에 따라 지식을 재사용하도록 만드는 것을 목표로 한다. 이는 인과 표현 학습(Causal Representation Learning), 인과 딥러닝(Causal Deep Learning), 인과 강화학습(Causal Reinforcement Learning), 인과 대규모 언어 모델(Causal LLMs)을 하나의 공통된 목표로 연결한다. 즉, 환경 변화에서도 유지되는 지식을 발견하는 것이며, 이러한 능력은 원래의 훈련 데이터가 포함하지 않았던 조건에서도 동작하고 추론하며 적응해야 하는 강건한 인공지능(robust AI) 시스템의 핵심 기반이 된다.
