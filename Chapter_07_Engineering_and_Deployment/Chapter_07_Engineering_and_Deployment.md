**Volume 46. Causality and Scientific AI**


# Chapter 07. Engineering and Deployment

##  

## 07.01. Data Pipeline [w/Code]

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

A data pipeline provides the operational foundation that transforms raw information into reliable inputs for causal analysis, model training, evaluation, and deployment. In engineering systems, data rarely arrives in a directly usable form. It must be collected, validated, synchronized, transformed, stored, versioned, and delivered through a repeatable process that preserves the information required for later reasoning.

The pipeline begins with data acquisition from observational, experimental, simulated, and operational sources. Depending on the application, these sources may include databases, logs, cameras, LiDAR, audio, telemetry, control commands, human annotations, language documents, and external knowledge. Acquisition must preserve relevant context because causal interpretation often depends on where, when, and under what conditions each observation was generated.

Data provenance is particularly important for causal systems. Every record should retain information about its origin, collection environment, sensor configuration, preprocessing history, intervention status, and relevant experimental conditions. Without provenance, observations gathered under fundamentally different mechanisms may be combined incorrectly, producing apparent relationships that reflect collection procedures rather than the underlying system being studied.

Temporal synchronization is essential whenever data represents dynamic processes. Different sensors and software components may operate at different frequencies, clocks, and communication latencies. Accurate timestamps, clock synchronization, buffering, interpolation, and latency compensation are required to reconstruct the true order of events. Incorrect temporal alignment can create false causal directions by making an effect appear to occur before its actual cause.

Raw data must then pass through validation and quality control. Missing values, corrupted records, duplicated samples, sensor saturation, inconsistent units, impossible states, and abnormal timestamps should be detected before they propagate downstream. Validation rules may combine statistical checks with physical constraints and domain knowledge. Importantly, unusual observations should not automatically be removed because rare events may contain valuable information about interventions, failures, or changing mechanisms.

Cleaning should preserve causal information rather than simply making datasets statistically convenient. Aggressive filtering can eliminate meaningful transitions, while normalization across environments can unintentionally erase differences required for causal discovery. Processing decisions should therefore distinguish measurement artifacts from genuine environmental variation. Original data should normally remain immutable so that alternative preprocessing strategies can later be evaluated without repeating collection.

Multimodal pipelines require explicit management of relationships among different data streams. Images, point clouds, audio, force signals, proprioception, actions, and semantic information may describe the same underlying event at different resolutions. Rather than storing them as unrelated datasets, the pipeline should preserve shared timestamps, episode identifiers, coordinate frames, entity references, and environmental metadata that allow observations to be reconstructed as coherent experiences.

Representation transformation converts raw measurements into formats suitable for learning. Images may be resized or encoded, point clouds voxelized, signals filtered, language tokenized, and structured variables normalized. Higher-level processing may extract objects, tracks, events, contacts, actions, or latent states. For causal learning, these transformations should preserve variables and relationships that may correspond to mechanisms rather than optimizing compression alone.

Episode construction is useful for sequential and embodied systems. Continuous streams can be organized into trajectories containing initial states, observations, actions, interventions, rewards, outcomes, and terminal conditions. Episodes provide natural units for reinforcement learning, world modeling, and counterfactual analysis. They also make it easier to separate independent experiences and prevent information from future states from leaking into training inputs representing the past.

Interventional data should be explicitly distinguished from observational data. An action deliberately selected by an agent differs fundamentally from a variable that merely happened to take a particular value. The pipeline should therefore record intervention targets, commanded actions, execution results, intervention timing, and relevant environmental conditions. This metadata enables downstream models to reason about action effects instead of treating every association as passive correlation.

Environmental context should also be represented as a first-class component of the dataset. Location, weather, lighting, terrain, payload, hardware configuration, software version, task type, operator behavior, and other contextual variables can alter observed distributions. Recording these factors enables models to compare environments, identify invariant mechanisms, detect domain shifts, and evaluate whether learned relationships generalize beyond the conditions used for training.

Dataset partitioning requires greater care for causal and sequential learning than ordinary random splitting. Randomly separating neighboring samples from the same trajectory can create leakage and produce unrealistically optimistic evaluation. Splits may instead be organized by episode, time period, environment, object category, intervention, robot, site, or operating condition. This allows evaluation to measure genuine transfer rather than memorization of nearly identical observations.

Storage architecture must support both large raw datasets and efficiently accessible training representations. Object storage can hold images, video, point clouds, and logs, while databases or structured metadata stores maintain indexes, labels, provenance, and relationships. Frequently accessed features may be cached in optimized formats. The architecture should separate immutable source data from derived datasets so that processing remains traceable and reproducible.

Dataset versioning is essential because data continuously evolves. New environments are added, labels are corrected, preprocessing algorithms change, and failed sensors may later be identified. Each training run should reference a reproducible dataset version rather than an ambiguous directory containing the latest files. Versioning links model behavior to the exact evidence used during training and makes regression analysis possible when performance changes.

Schema management provides consistency as pipelines evolve. A schema defines variables, data types, units, coordinate systems, required metadata, allowed ranges, and relationships among records. Changes should be explicitly versioned because silently modifying a field can invalidate previously trained models. Strong schemas are particularly important in multimodal systems where multiple teams and software components contribute data over long development cycles.

Scalable processing becomes necessary when datasets grow from gigabytes to terabytes or petabytes. Expensive operations such as decoding video, transforming point clouds, generating embeddings, or constructing trajectories can be parallelized across CPUs, GPUs, or distributed workers. Incremental processing avoids recomputing unchanged data, while caching and partitioning reduce unnecessary transfers between storage and compute resources.

Streaming pipelines extend this architecture to continuously operating systems. Robots, vehicles, industrial equipment, and online services generate new observations while deployed. Streaming infrastructure can validate, summarize, and store incoming data while identifying important episodes for later training. The pipeline can prioritize anomalies, failures, uncertain situations, and novel environments instead of retaining every repetitive observation at identical resolution and priority.

Data selection becomes increasingly important as collection scales. More data does not automatically produce better models when most observations are redundant. Sampling can emphasize rare events, interventions, distribution shifts, uncertain predictions, or poorly understood mechanisms. Active learning can further identify which additional examples or experiments would provide the greatest information, connecting the data pipeline directly with model uncertainty and causal discovery.

Simulation provides another data source and should be integrated without obscuring its origin. Synthetic environments can generate rare failures, controlled interventions, counterfactual scenarios, and combinations that are difficult or dangerous to collect physically. Simulation metadata should record scenario parameters and model assumptions so that synthetic evidence can be distinguished from real observations and sim-to-real discrepancies can be measured explicitly.

Annotation pipelines transform raw observations into supervised or weakly supervised training signals. Labels may originate from humans, algorithms, foundation models, simulation ground truth, or cross-sensor inference. Each annotation should retain its source and confidence because automatically generated labels are not equivalent to verified ground truth. Weak supervision can scale labeling while uncertainty information prevents noisy annotations from being treated as unquestionable facts.

Privacy, security, and governance must be incorporated into pipeline design rather than added after deployment. Access control, encryption, retention policies, audit logs, anonymization, and data licensing determine who can use particular information and for what purposes. Sensitive or restricted data may require separate storage and processing paths. Governance metadata should travel with datasets so that downstream systems can enforce appropriate usage constraints.

Monitoring is necessary because a production data pipeline is itself a changing system. Sensor failures, schema drift, missing fields, unexpected distributions, storage corruption, processing delays, and software updates can silently alter training data. Automated monitoring should track data quality, volume, latency, environmental coverage, class balance, intervention frequency, and other relevant characteristics so that changes are detected before they degrade models.

The pipeline should ultimately connect deployment back to learning through a closed feedback loop. Models operating in the real world generate predictions, uncertainty estimates, actions, successes, and failures that become new data. Selected experiences return to storage, validation, annotation, and training, while updated models are evaluated before redeployment. This creates a continuous cycle of collection, learning, evaluation, deployment, and renewed observation.

For Physical AI, this feedback loop is especially important because the data distribution changes as robots enter new environments and perform new behaviors. A well-engineered pipeline preserves synchronized multimodal observations, actions, interventions, environmental context, and outcomes as structured experience. It therefore becomes more than data infrastructure: it forms the persistent evidence layer from which world models, causal models, policies, and autonomous systems can continually improve.

데이터 파이프라인(Data Pipeline)은 원시 정보(raw information)를 인과 분석(causal analysis), 모델 학습(model training), 평가(evaluation), 배포(deployment)에 사용할 수 있는 신뢰성 높은 입력으로 변환하는 운영 기반을 제공한다. 엔지니어링 시스템에서 데이터는 거의 항상 직접 사용할 수 없는 형태로 들어온다. 따라서 이후의 추론에 필요한 정보를 보존하면서 데이터를 수집하고, 검증하고, 동기화하고, 변환하고, 저장하고, 버전 관리하며, 반복 가능한 과정을 통해 전달해야 한다.

파이프라인은 관측 데이터(observational data), 실험 데이터(experimental data), 시뮬레이션 데이터(simulated data), 운영 데이터(operational data)로부터의 데이터 획득(data acquisition)으로 시작된다. 응용 분야에 따라 데이터 소스에는 데이터베이스, 로그, 카메라, 라이다(LiDAR), 오디오, 텔레메트리(telemetry), 제어 명령, 인간 주석(human annotation), 언어 문서 및 외부 지식이 포함될 수 있다. 인과적 해석은 각 관측이 언제, 어디에서, 어떤 조건에서 생성되었는지에 의존하는 경우가 많으므로 획득 단계에서 관련 맥락을 보존해야 한다.

데이터 출처 추적(data provenance)은 인과 시스템에서 특히 중요하다. 각각의 기록은 데이터의 출처, 수집 환경, 센서 구성, 전처리 이력(preprocessing history), 개입 상태(intervention status), 관련 실험 조건에 대한 정보를 유지해야 한다. 출처 정보가 없으면 근본적으로 서로 다른 메커니즘에서 수집된 관측을 잘못 결합할 수 있으며, 이로 인해 실제 시스템의 기반 구조가 아니라 데이터 수집 절차 자체를 반영하는 관계가 나타날 수 있다.

데이터가 동적인 과정을 표현하는 경우 시간 동기화(temporal synchronization)가 필수적이다. 서로 다른 센서와 소프트웨어 구성 요소는 서로 다른 주파수, 클록(clock), 통신 지연 시간으로 동작할 수 있다. 사건의 실제 발생 순서를 복원하려면 정확한 타임스탬프(timestamp), 클록 동기화(clock synchronization), 버퍼링(buffering), 보간(interpolation), 지연 보상(latency compensation)이 필요하다. 잘못된 시간 정렬은 결과가 실제 원인보다 먼저 발생한 것처럼 보이게 하여 잘못된 인과 방향(false causal direction)을 만들어낼 수 있다.

원시 데이터(raw data)는 이후 검증(validation)과 품질 관리(quality control) 과정을 거쳐야 한다. 누락 값(missing value), 손상된 기록, 중복 샘플, 센서 포화(sensor saturation), 일관되지 않은 단위, 불가능한 상태, 비정상적인 타임스탬프 등을 탐지하여 이후 단계로 전파되는 것을 방지해야 한다. 검증 규칙은 통계적 검사와 물리적 제약 및 도메인 지식(domain knowledge)을 결합할 수 있다. 특히 드문 사건은 개입, 고장 또는 메커니즘 변화에 관한 중요한 정보를 포함할 수 있으므로 비정상적이라는 이유만으로 자동 제거해서는 안 된다.

데이터 정제(cleaning)는 단순히 데이터셋을 통계적으로 편리하게 만드는 것이 아니라 인과 정보를 보존해야 한다. 과도한 필터링(aggressive filtering)은 의미 있는 상태 전이를 제거할 수 있으며, 환경 전체에 일괄적으로 적용되는 정규화(normalization)는 인과 발견에 필요한 환경 차이를 의도치 않게 제거할 수 있다. 따라서 처리 과정에서는 측정 인공물(measurement artifact)과 실제 환경 변화를 구별해야 한다. 또한 다른 전처리 전략을 데이터 재수집 없이 평가할 수 있도록 원본 데이터는 일반적으로 변경 불가능한 형태(immutable form)로 보존하는 것이 바람직하다.

다중 모달 파이프라인(multimodal pipeline)은 서로 다른 데이터 스트림 사이의 관계를 명시적으로 관리해야 한다. 이미지, 포인트 클라우드(point cloud), 오디오, 힘 신호, 고유수용감각(proprioception), 행동 및 의미 정보는 서로 다른 해상도에서 동일한 기반 사건을 설명할 수 있다. 따라서 이를 서로 관련 없는 데이터셋으로 저장하기보다 공유 타임스탬프, 에피소드 식별자(episode identifier), 좌표계(coordinate frame), 개체 참조(entity reference), 환경 메타데이터(environmental metadata)를 보존하여 관측을 일관된 경험으로 재구성할 수 있도록 해야 한다.

표현 변환(representation transformation)은 원시 측정값을 학습에 적합한 형식으로 변환한다. 이미지는 크기 조정 또는 인코딩되고, 포인트 클라우드는 복셀화(voxelization)되며, 신호는 필터링되고, 언어는 토큰화(tokenization)되며, 구조화 변수는 정규화될 수 있다. 상위 수준의 처리에서는 객체, 추적 정보(track), 사건, 접촉, 행동 또는 잠재 상태(latent state)를 추출할 수 있다. 인과 학습에서는 단순한 압축만을 최적화하기보다 메커니즘에 대응할 가능성이 있는 변수와 관계를 보존해야 한다.

에피소드 구성(episode construction)은 순차 시스템(sequential system)과 체화 시스템(embodied system)에서 유용하다. 연속적인 데이터 스트림을 초기 상태, 관측, 행동, 개입, 보상, 결과 및 종료 조건(terminal condition)을 포함하는 궤적(trajectory)으로 구성할 수 있다. 에피소드는 강화학습(reinforcement learning), 월드 모델링(world modeling), 반사실적 분석(counterfactual analysis)을 위한 자연스러운 단위를 제공한다. 또한 독립적인 경험을 분리하고 미래 상태의 정보가 과거를 나타내는 학습 입력으로 유출되는 것을 방지하는 데 도움이 된다.

개입 데이터(interventional data)는 관측 데이터와 명확하게 구분해야 한다. 에이전트가 의도적으로 선택한 행동은 특정 변수가 우연히 특정 값을 가진 것과 근본적으로 다르다. 따라서 파이프라인은 개입 대상(intervention target), 명령된 행동(commanded action), 실행 결과, 개입 시점, 관련 환경 조건을 기록해야 한다. 이러한 메타데이터(metadata)를 통해 후속 모델은 모든 연관성을 수동적인 상관관계로 취급하지 않고 행동의 효과(action effect)를 추론할 수 있다.

환경 맥락(environmental context) 역시 데이터셋의 핵심 구성 요소로 표현되어야 한다. 위치, 날씨, 조명, 지형, 페이로드(payload), 하드웨어 구성, 소프트웨어 버전, 작업 유형, 운영자 행동 및 기타 맥락 변수는 관측된 분포를 변화시킬 수 있다. 이러한 요인을 기록하면 모델이 여러 환경을 비교하고, 불변 메커니즘(invariant mechanism)을 식별하며, 도메인 변화(domain shift)를 탐지하고, 학습된 관계가 훈련 조건을 넘어 일반화되는지를 평가할 수 있다.

데이터셋 분할(dataset partitioning)은 일반적인 무작위 분할보다 인과 학습 및 순차 학습에서 더욱 신중하게 수행해야 한다. 동일한 궤적에서 서로 인접한 샘플을 무작위로 분리하면 데이터 누출(data leakage)이 발생하여 비현실적으로 높은 평가 결과를 만들 수 있다. 대신 에피소드, 시간 구간, 환경, 객체 범주, 개입, 로봇, 장소 또는 운영 조건을 기준으로 데이터를 분할할 수 있다. 이를 통해 거의 동일한 관측을 암기하는 것이 아니라 실제 전이 능력(transfer capability)을 평가할 수 있다.

저장 아키텍처(storage architecture)는 대규모 원시 데이터와 학습 과정에서 효율적으로 접근할 수 있는 표현을 모두 지원해야 한다. 객체 저장소(object storage)는 이미지, 비디오, 포인트 클라우드 및 로그를 보관할 수 있고, 데이터베이스 또는 구조화 메타데이터 저장소는 인덱스, 라벨, 출처 정보 및 관계를 관리할 수 있다. 자주 사용되는 특징(feature)은 최적화된 형식으로 캐싱(caching)할 수 있다. 처리 과정의 추적성과 재현성(reproducibility)을 유지하려면 변경되지 않는 원본 데이터와 파생 데이터셋(derived dataset)을 분리해야 한다.

데이터는 지속적으로 변화하므로 데이터셋 버전 관리(dataset versioning)가 필수적이다. 새로운 환경이 추가되고, 라벨이 수정되고, 전처리 알고리즘이 변경되며, 이전에는 알지 못했던 센서 고장이 나중에 발견될 수 있다. 각각의 학습 실행(training run)은 단순히 최신 파일이 들어 있는 모호한 디렉터리가 아니라 재현 가능한 특정 데이터셋 버전을 참조해야 한다. 버전 관리는 모델의 동작을 학습에 실제 사용된 정확한 증거와 연결하며, 성능 변화가 발생했을 때 회귀 분석(regression analysis)을 가능하게 한다.

스키마 관리(schema management)는 파이프라인이 발전하더라도 데이터의 일관성을 유지한다. 스키마(schema)는 변수, 데이터 유형, 단위, 좌표계, 필수 메타데이터, 허용 범위 및 기록 사이의 관계를 정의한다. 필드가 조용히 변경되면 이전에 학습된 모델이 무효화될 수 있으므로 변경 사항 역시 명시적으로 버전 관리해야 한다. 강력한 스키마는 여러 팀과 소프트웨어 구성 요소가 장기간 데이터를 생성하는 다중 모달 시스템에서 특히 중요하다.

데이터셋의 규모가 기가바이트에서 테라바이트 또는 페타바이트로 증가하면 확장 가능한 처리(scalable processing)가 필요하다. 비디오 디코딩, 포인트 클라우드 변환, 임베딩(embedding) 생성, 궤적 구성과 같이 계산 비용이 높은 작업은 CPU, GPU 또는 분산 작업자(distributed worker)에 병렬화할 수 있다. 증분 처리(incremental processing)는 변경되지 않은 데이터를 반복 계산하지 않도록 하며, 캐싱과 파티셔닝(partitioning)은 저장소와 컴퓨팅 자원 사이의 불필요한 데이터 이동을 줄인다.

스트리밍 파이프라인(streaming pipeline)은 이러한 아키텍처를 지속적으로 동작하는 시스템으로 확장한다. 로봇, 차량, 산업 장비 및 온라인 서비스는 배포된 상태에서도 새로운 관측을 계속 생성한다. 스트리밍 인프라는 들어오는 데이터를 검증하고 요약하며 저장하는 동시에 이후 학습에 중요한 에피소드를 식별할 수 있다. 모든 반복 관측을 동일한 해상도와 우선순위로 보존하는 대신 이상 상황, 고장, 불확실한 상황 및 새로운 환경을 우선적으로 선택할 수 있다.

데이터 수집 규모가 증가할수록 데이터 선택(data selection)이 더욱 중요해진다. 대부분의 관측이 중복된다면 단순히 데이터 양을 늘리는 것이 자동으로 더 좋은 모델을 만드는 것은 아니다. 샘플링(sampling)은 희귀 사건, 개입, 분포 변화(distribution shift), 불확실한 예측 또는 충분히 이해되지 않은 메커니즘을 강조할 수 있다. 능동 학습(active learning)은 어떤 추가 사례나 실험이 가장 많은 정보를 제공할지를 식별하여 데이터 파이프라인을 모델 불확실성과 인과 발견(causal discovery)에 직접 연결할 수 있다.

시뮬레이션(simulation)은 또 다른 데이터 소스를 제공하며 그 출처가 불분명해지지 않도록 통합해야 한다. 합성 환경(synthetic environment)은 실제 환경에서 수집하기 어렵거나 위험한 희귀 고장, 통제된 개입, 반사실적 시나리오(counterfactual scenario), 다양한 조건의 조합을 생성할 수 있다. 시뮬레이션 메타데이터는 시나리오 매개변수와 모델 가정을 기록하여 합성 증거와 실제 관측을 구별하고 시뮬레이션-현실 차이(sim-to-real discrepancy)를 명시적으로 측정할 수 있도록 해야 한다.

주석 파이프라인(annotation pipeline)은 원시 관측을 지도학습(supervised learning) 또는 약지도 학습(weakly supervised learning)을 위한 학습 신호로 변환한다. 라벨(label)은 인간, 알고리즘, 파운데이션 모델(Foundation Model), 시뮬레이션 정답(simulation ground truth), 교차 센서 추론(cross-sensor inference) 등에서 생성될 수 있다. 자동 생성 라벨은 검증된 정답과 동일하지 않으므로 각 주석은 출처와 신뢰도(confidence)를 유지해야 한다. 약지도 학습은 라벨링 규모를 확장할 수 있으며, 불확실성 정보는 잡음이 있는 주석이 절대적인 사실처럼 취급되는 것을 방지한다.

개인정보 보호(privacy), 보안(security), 거버넌스(governance)는 배포 이후에 추가되는 기능이 아니라 파이프라인 설계 단계부터 포함되어야 한다. 접근 제어(access control), 암호화(encryption), 보존 정책(retention policy), 감사 로그(audit log), 익명화(anonymization), 데이터 라이선스는 특정 정보를 누가 어떤 목적으로 사용할 수 있는지를 결정한다. 민감하거나 제한된 데이터는 별도의 저장 및 처리 경로가 필요할 수 있으며, 후속 시스템이 적절한 사용 제약을 적용할 수 있도록 거버넌스 메타데이터도 데이터셋과 함께 전달되어야 한다.

운영 환경의 데이터 파이프라인 자체도 지속적으로 변화하는 시스템이므로 모니터링(monitoring)이 필요하다. 센서 고장, 스키마 드리프트(schema drift), 누락 필드, 예상하지 못한 분포, 저장 데이터 손상, 처리 지연, 소프트웨어 업데이트는 학습 데이터를 조용히 변화시킬 수 있다. 자동화된 모니터링은 데이터 품질, 데이터 양, 지연 시간, 환경 커버리지(environmental coverage), 클래스 균형(class balance), 개입 빈도 및 기타 관련 특성을 추적하여 모델 성능이 저하되기 전에 변화를 발견해야 한다.

궁극적으로 파이프라인은 폐쇄형 피드백 루프(closed feedback loop)를 통해 배포를 다시 학습과 연결해야 한다. 실제 환경에서 동작하는 모델은 예측, 불확실성 추정, 행동, 성공 및 실패를 생성하며 이것이 다시 새로운 데이터가 된다. 선택된 경험은 저장, 검증, 주석 및 학습 과정으로 돌아가고, 업데이트된 모델은 다시 배포되기 전에 평가된다. 이를 통해 수집(collection), 학습(learning), 평가(evaluation), 배포(deployment), 새로운 관측(observation)이 지속적으로 반복되는 순환 구조가 형성된다.

피지컬 인공지능(Physical AI)에서는 로봇이 새로운 환경에 진입하고 새로운 행동을 수행하면서 데이터 분포가 계속 변화하기 때문에 이러한 피드백 루프가 특히 중요하다. 잘 설계된 데이터 파이프라인은 동기화된 다중 모달 관측, 행동, 개입, 환경 맥락 및 결과를 구조화된 경험(structured experience)으로 보존한다. 따라서 데이터 파이프라인은 단순한 데이터 인프라를 넘어 월드 모델(world model), 인과 모델(causal model), 정책(policy), 자율 시스템(autonomous system)이 지속적으로 발전할 수 있도록 경험과 증거를 축적하는 영속적인 증거 계층(persistent evidence layer)이 된다.

##  

## 07.02. Causal Model Pipeline [w/Code]

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

A causal model pipeline transforms curated data into a structured system capable of discovering, estimating, validating, and deploying causal relationships. Unlike a conventional machine-learning pipeline focused primarily on predictive accuracy, it must preserve assumptions about interventions, temporal order, confounding, environments, and mechanisms. Each stage therefore contributes evidence needed to distinguish statistical association from plausible causal influence.

The pipeline begins by defining the causal question rather than immediately selecting an algorithm. Engineers specify outcomes, candidate causes, intervention variables, relevant contexts, and the decisions the model must support. Questions such as whether X causes Y, how strongly an action changes an outcome, or what would happen under an alternative intervention require different modeling strategies and different forms of evidence.

Domain knowledge provides an initial structural foundation. Physical laws, engineering constraints, temporal ordering, system architecture, expert knowledge, and operational rules can eliminate impossible causal directions and identify plausible dependencies. These assumptions should be documented explicitly because causal conclusions depend not only on data but also on the structural conditions under which relationships are considered identifiable.

The next stage converts observations into candidate causal variables. Raw images, sensor signals, language, logs, actions, and contextual information may first require representation learning or feature extraction. Variables should correspond as closely as possible to meaningful entities, states, mechanisms, actions, and environmental factors. Poor representations can hide true mechanisms or create artificial dependencies that later appear causal.

Temporal structure must be established for dynamic systems. Variables are aligned using synchronized timestamps, and appropriate time lags are identified between possible causes and effects. Immediate interactions, delayed consequences, feedback loops, and persistent states may require different representations. Temporal constraints can reduce the number of possible causal graphs, although temporal precedence alone cannot prove that one variable causes another.

Potential confounders must then be identified. A variable influencing both a candidate cause and an outcome can generate an association even when no direct causal relationship exists between them. Observed confounders may be included explicitly in the model, while hidden confounding requires stronger assumptions, latent-variable methods, instrumental information, natural experiments, or controlled interventions when available.

Causal graph construction organizes variables and assumptions into a structural representation. Nodes describe variables or latent states, while directed edges encode hypothesized causal influence. Some edges may be supplied by prior knowledge, others discovered from data, and others deliberately left uncertain. The resulting graph becomes a working hypothesis rather than an unquestionable description of the underlying system.

Causal discovery algorithms can refine this structure by testing statistical independencies, optimizing graph scores, exploiting functional relationships, or analyzing changes across environments. Constraint-based, score-based, functional, continuous-optimization, and neural approaches provide different tradeoffs. No discovery algorithm can universally recover causal truth, so its assumptions must match the characteristics of the available data.

Interventional data substantially strengthens causal discovery. When a variable is deliberately manipulated, the resulting distribution can reveal relationships that remain ambiguous in observational data. Experiments, randomized actions, robot commands, controlled parameter changes, and operational interventions can therefore be incorporated into the pipeline. Observational and interventional samples should remain distinguishable throughout modeling.

Once a plausible structure has been obtained, causal effect estimation quantifies how interventions influence outcomes. Depending on the problem, the pipeline may estimate average treatment effects, conditional effects, individual effects, mediated effects, or dynamic action effects. Adjustment sets derived from the causal structure determine which variables should be controlled rather than simply including every available feature in a predictive model.

Structural causal models can represent these relationships through explicit mechanisms. Each variable is described as a function of its causal parents and external disturbances. This formulation enables the pipeline to move from association toward intervention and counterfactual reasoning. Learned structural equations may use linear functions, probabilistic models, neural networks, Gaussian processes, or other approximators depending on the complexity of the mechanism.

Counterfactual modeling adds the ability to reason about alternative outcomes for previously observed situations. The model first infers hidden conditions compatible with the actual observation, replaces the relevant action or condition with a hypothetical intervention, and then propagates the modified mechanisms forward. This supports diagnosis, explanation, policy comparison, failure analysis, and decision improvement.

Uncertainty estimation must accompany causal predictions. Uncertainty can arise from limited data, noisy observations, uncertain graph structure, hidden variables, model misspecification, or unfamiliar environments. Instead of returning only one causal estimate, the pipeline should preserve confidence intervals, posterior distributions, alternative graph hypotheses, or calibrated uncertainty measures where appropriate.

Validation is fundamentally different from ordinary predictive evaluation. A model may accurately predict Y from X while representing the causal relationship incorrectly. Whenever possible, causal hypotheses should therefore be tested against held-out interventions, controlled experiments, known mechanisms, natural experiments, or environment changes. Predictive accuracy remains useful, but it cannot by itself establish causal validity.

Robustness across environments provides another important validation signal. Genuine mechanisms often remain more stable than superficial correlations when lighting, location, population, hardware, policies, objects, or operating conditions change. Evaluating causal relationships across such shifts can expose dependencies that worked only in the training environment and identify mechanisms with stronger generalization potential.

Sensitivity analysis examines how conclusions change when assumptions are weakened. Engineers can vary adjustment sets, model structures, hidden-confounding assumptions, measurement noise, intervention strength, or functional forms. If small changes produce radically different conclusions, the causal result should be treated cautiously. Stable conclusions across reasonable assumptions provide stronger evidence for downstream decisions.

Model selection should therefore consider causal validity, interpretability, uncertainty, computational cost, and operational requirements together. A simple structural model may be preferable when mechanisms are well understood and explanation is critical, while flexible neural causal models may be necessary for high-dimensional nonlinear systems. Hybrid architectures can combine explicit causal structure with learned components.

For sequential decision systems, the causal model can be connected to a world model. Observations estimate the current state, actions are represented as interventions, causal transition mechanisms predict future states, and candidate action sequences are simulated internally. This converts the causal model from a static analytical tool into an operational component for planning, control, and autonomous decision making.

Model-based reinforcement learning can further exploit this structure. Instead of learning policies solely from rewards and observed transitions, an agent can use causal mechanisms to predict the effects of alternative actions. Exploration can target uncertain causal relationships, making new experiences informative about both task performance and the structure of the environment.

Deployment requires packaging the causal model together with its preprocessing, variable definitions, graph structure, assumptions, confidence information, and model version. An inference service should receive data generated under compatible conditions and return not only estimates but also relevant uncertainty and applicability information. Deploying a causal model without its assumptions can lead users to interpret conditional predictions as universal causal conclusions.

Monitoring must continue after deployment because causal mechanisms can change. Hardware degradation, new populations, environmental changes, policy modifications, software updates, or altered human behavior may invalidate previously stable relationships. Monitoring should therefore track input distributions, causal residuals, intervention outcomes, mechanism stability, uncertainty, and violations of expected structural relationships.

Unexpected outcomes provide valuable evidence for model revision. When observed consequences disagree with causal predictions, the system should determine whether the problem originates from measurement error, distribution shift, an incorrect structural edge, an inaccurate mechanism, or a previously hidden variable. These failures can be returned to the data and modeling pipeline as targeted examples for further investigation.

Versioning is especially important because causal models contain more than learned parameters. A complete version should include the dataset, variable schema, graph topology, structural assumptions, preprocessing logic, intervention definitions, estimation method, validation results, and uncertainty configuration. This makes it possible to reproduce conclusions and determine why two model versions produce different causal recommendations.

Human review remains important in high-impact applications. Experts can examine whether discovered relationships are physically, operationally, or scientifically plausible and identify assumptions that algorithms cannot verify from data. Human judgment should not replace empirical validation, but it can prevent statistically attractive yet impossible causal structures from progressing directly into operational decision systems.

For Physical AI, the causal model pipeline can operate continuously between data infrastructure and autonomous intelligence. Multimodal experience provides observations, robot actions provide interventions, causal discovery identifies candidate mechanisms, structural models predict consequences, and planners evaluate alternative actions. Deployment then generates new interaction data that can confirm, challenge, or refine the current causal model.

The complete pipeline therefore forms a closed causal learning cycle: define causal questions, construct meaningful variables, propose structure, discover relationships, estimate intervention effects, validate mechanisms, deploy models, observe consequences, and revise assumptions. Its purpose is not merely to predict what usually happens, but to build increasingly reliable models of why events occur and how deliberate actions can change future outcomes.

인과 모델 파이프라인(Causal Model Pipeline)은 정제된 데이터(curated data)를 인과관계를 발견하고, 추정하고, 검증하고, 배포할 수 있는 구조화된 시스템으로 변환한다. 주로 예측 정확도(predictive accuracy)에 초점을 맞추는 일반적인 머신러닝 파이프라인(machine-learning pipeline)과 달리, 개입(intervention), 시간적 순서(temporal order), 교란(confounding), 환경(environment), 메커니즘(mechanism)에 관한 가정을 보존해야 한다. 따라서 각 단계는 통계적 연관성(statistical association)과 타당한 인과적 영향(causal influence)을 구별하는 데 필요한 증거를 제공한다.

파이프라인은 알고리즘을 즉시 선택하는 것이 아니라 인과 질문(causal question)을 정의하는 것에서 시작한다. 엔지니어는 결과(outcome), 후보 원인(candidate cause), 개입 변수(intervention variable), 관련 맥락(context), 그리고 모델이 지원해야 하는 의사결정을 명확하게 정의한다. X가 Y를 발생시키는지, 특정 행동이 결과를 얼마나 변화시키는지, 또는 다른 개입이 이루어졌다면 어떤 일이 발생했을지를 묻는 질문은 서로 다른 모델링 전략과 서로 다른 형태의 증거를 필요로 한다.

도메인 지식(domain knowledge)은 초기 구조적 기반을 제공한다. 물리 법칙, 공학적 제약(engineering constraint), 시간적 순서, 시스템 아키텍처(system architecture), 전문가 지식, 운영 규칙을 이용하여 불가능한 인과 방향을 제거하고 타당한 의존관계를 식별할 수 있다. 인과적 결론은 데이터뿐만 아니라 관계를 식별 가능하다고 판단하는 구조적 조건에도 의존하므로 이러한 가정은 명시적으로 문서화되어야 한다.

다음 단계에서는 관측을 후보 인과 변수(candidate causal variable)로 변환한다. 원시 이미지, 센서 신호, 언어, 로그, 행동, 맥락 정보는 먼저 표현 학습(representation learning) 또는 특징 추출(feature extraction)을 필요로 할 수 있다. 변수는 가능한 한 의미 있는 개체(entity), 상태(state), 메커니즘, 행동, 환경 요인에 대응해야 한다. 잘못된 표현은 실제 메커니즘을 숨기거나 이후 인과적인 것으로 보이는 인위적인 의존관계를 만들어낼 수 있다.

동적 시스템(dynamic system)에서는 시간 구조(temporal structure)를 설정해야 한다. 동기화된 타임스탬프(timestamp)를 이용하여 변수를 정렬하고 가능한 원인과 결과 사이의 적절한 시간 지연(time lag)을 식별한다. 즉각적인 상호작용, 지연된 결과(delayed consequence), 피드백 루프(feedback loop), 지속 상태(persistent state)는 서로 다른 표현을 필요로 할 수 있다. 시간적 제약은 가능한 인과 그래프의 수를 줄일 수 있지만, 시간적으로 먼저 발생했다는 사실만으로 인과관계를 증명할 수는 없다.

이후 잠재적 교란 요인(potential confounder)을 식별해야 한다. 후보 원인과 결과 모두에 영향을 미치는 변수는 이들 사이에 직접적인 인과관계가 존재하지 않더라도 연관성을 만들어낼 수 있다. 관측된 교란 요인(observed confounder)은 모델에 명시적으로 포함할 수 있지만, 숨겨진 교란(hidden confounding)은 더 강력한 가정, 잠재 변수 방법(latent-variable method), 도구 변수 정보(instrumental information), 자연 실험(natural experiment), 또는 가능한 경우 통제된 개입(controlled intervention)을 필요로 한다.

인과 그래프 구성(causal graph construction)은 변수와 가정을 구조화된 표현으로 조직한다. 노드(node)는 변수 또는 잠재 상태(latent state)를 나타내고, 방향성 간선(directed edge)은 가정된 인과적 영향을 표현한다. 일부 간선은 사전 지식(prior knowledge)으로 제공되고, 일부는 데이터에서 발견되며, 다른 일부는 의도적으로 불확실한 상태로 남겨둘 수 있다. 이렇게 생성된 그래프는 기반 시스템에 대한 절대적인 설명이 아니라 검증되어야 할 작업 가설(working hypothesis)이 된다.

인과 발견 알고리즘(causal discovery algorithm)은 통계적 독립성(statistical independence)을 검정하고, 그래프 점수(graph score)를 최적화하며, 함수적 관계(functional relationship)를 활용하거나, 여러 환경에서 발생하는 변화를 분석하여 이러한 구조를 개선할 수 있다. 제약 기반(constraint-based), 점수 기반(score-based), 함수 기반(functional), 연속 최적화(continuous optimization), 신경망 기반(neural) 접근법은 각각 서로 다른 장단점을 가진다. 어떤 인과 발견 알고리즘도 모든 상황에서 인과적 진실을 복원할 수 없으므로 알고리즘의 가정은 사용 가능한 데이터의 특성과 일치해야 한다.

개입 데이터(interventional data)는 인과 발견을 크게 강화한다. 하나의 변수를 의도적으로 조작하면 그 결과 발생하는 분포 변화를 통해 관측 데이터만으로는 모호하게 남아 있던 관계를 밝힐 수 있다. 실험, 무작위 행동(randomized action), 로봇 명령(robot command), 통제된 매개변수 변경, 운영상의 개입을 파이프라인에 포함할 수 있다. 관측 샘플과 개입 샘플은 전체 모델링 과정에서 명확하게 구별되어야 한다.

타당한 구조가 확보되면 인과 효과 추정(causal effect estimation)을 통해 개입이 결과에 얼마나 영향을 주는지를 정량화한다. 문제에 따라 평균 처치 효과(Average Treatment Effect, ATE), 조건부 효과(conditional effect), 개별 효과(individual effect), 매개 효과(mediated effect), 동적 행동 효과(dynamic action effect)를 추정할 수 있다. 인과 구조에서 도출된 조정 집합(adjustment set)은 예측 모델처럼 사용 가능한 모든 특징을 단순히 포함하는 것이 아니라 어떤 변수를 통제해야 하는지를 결정한다.

구조적 인과 모델(Structural Causal Model, SCM)은 이러한 관계를 명시적인 메커니즘으로 표현할 수 있다. 각각의 변수는 자신의 인과 부모(causal parent)와 외부 교란(external disturbance)의 함수로 설명된다. 이러한 공식화는 파이프라인이 단순한 연관성에서 개입과 반사실적 추론(counterfactual reasoning)으로 발전할 수 있도록 한다. 학습된 구조 방정식(structural equation)은 메커니즘의 복잡성에 따라 선형 함수, 확률 모델, 신경망, 가우시안 프로세스(Gaussian Process) 또는 기타 근사기를 사용할 수 있다.

반사실적 모델링(counterfactual modeling)은 이미 관측된 상황에서 다른 결과가 발생했을 가능성을 추론하는 능력을 추가한다. 모델은 먼저 실제 관측과 일치하는 숨겨진 조건(hidden condition)을 추론하고, 관련된 행동이나 조건을 가상의 개입으로 대체한 후 수정된 메커니즘을 미래로 전파한다. 이는 진단(diagnosis), 설명(explanation), 정책 비교(policy comparison), 고장 분석(failure analysis), 의사결정 개선을 지원한다.

불확실성 추정(uncertainty estimation)은 인과 예측과 함께 수행되어야 한다. 제한된 데이터, 잡음이 있는 관측, 불확실한 그래프 구조, 숨겨진 변수, 모델 명세 오류(model misspecification), 익숙하지 않은 환경 등으로 인해 불확실성이 발생할 수 있다. 따라서 파이프라인은 하나의 인과 추정값만 반환하기보다 상황에 따라 신뢰 구간(confidence interval), 사후 분포(posterior distribution), 대안적인 그래프 가설(alternative graph hypothesis), 또는 보정된 불확실성 척도(calibrated uncertainty measure)를 보존해야 한다.

검증(validation)은 일반적인 예측 평가와 근본적으로 다르다. 모델이 X를 이용하여 Y를 정확하게 예측하더라도 실제 인과관계를 잘못 표현할 수 있다. 따라서 가능한 경우 인과 가설은 별도로 유지한 개입 데이터(held-out intervention), 통제 실험(controlled experiment), 알려진 메커니즘, 자연 실험 또는 환경 변화를 이용하여 검증해야 한다. 예측 정확도 역시 유용하지만 그것만으로 인과적 타당성(causal validity)을 확립할 수는 없다.

환경 사이의 강건성(robustness)은 또 다른 중요한 검증 신호를 제공한다. 실제 메커니즘은 조명, 위치, 모집단(population), 하드웨어, 정책, 객체 또는 운영 조건이 변화하더라도 표면적인 상관관계보다 안정적으로 유지되는 경우가 많다. 이러한 변화에 걸쳐 인과관계를 평가하면 훈련 환경에서만 작동했던 의존관계를 발견하고, 더 높은 일반화 가능성을 가진 메커니즘을 식별할 수 있다.

민감도 분석(sensitivity analysis)은 가정을 완화했을 때 결론이 어떻게 변화하는지를 검토한다. 엔지니어는 조정 집합, 모델 구조, 숨겨진 교란에 관한 가정, 측정 잡음, 개입 강도(intervention strength), 함수 형태(functional form)를 변경할 수 있다. 작은 변화만으로 결론이 크게 달라진다면 해당 인과 결과는 신중하게 다루어야 한다. 합리적인 가정 범위에서 안정적으로 유지되는 결론은 후속 의사결정을 위한 더욱 강력한 증거를 제공한다.

따라서 모델 선택(model selection)은 인과적 타당성, 해석 가능성(interpretability), 불확실성, 계산 비용, 운영 요구사항을 함께 고려해야 한다. 메커니즘이 충분히 이해되고 설명이 중요한 경우에는 단순한 구조 모델(structural model)이 더 적합할 수 있으며, 고차원 비선형 시스템에는 유연한 신경망 인과 모델(neural causal model)이 필요할 수 있다. 하이브리드 아키텍처(hybrid architecture)는 명시적인 인과 구조와 학습 기반 구성 요소를 결합할 수 있다.

순차적 의사결정 시스템(sequential decision system)에서는 인과 모델을 월드 모델(world model)과 연결할 수 있다. 관측은 현재 상태를 추정하고, 행동은 개입으로 표현되며, 인과 전이 메커니즘(causal transition mechanism)은 미래 상태를 예측하고, 후보 행동 시퀀스는 내부적으로 시뮬레이션된다. 이를 통해 인과 모델은 정적인 분석 도구에서 계획(planning), 제어(control), 자율 의사결정(autonomous decision making)을 위한 운영 구성 요소로 전환된다.

모델 기반 강화학습(Model-Based Reinforcement Learning)은 이러한 구조를 더욱 적극적으로 활용할 수 있다. 에이전트는 보상과 관측된 상태 전이만으로 정책을 학습하는 대신 인과 메커니즘을 이용하여 대안적인 행동의 효과를 예측할 수 있다. 탐색(exploration)은 불확실한 인과관계를 대상으로 수행될 수 있으며, 새로운 경험은 작업 성능뿐만 아니라 환경의 인과 구조를 이해하는 데에도 유용한 정보를 제공하게 된다.

배포(deployment)를 위해서는 인과 모델을 전처리 과정, 변수 정의, 그래프 구조, 가정, 신뢰도 정보, 모델 버전과 함께 패키징해야 한다. 추론 서비스(inference service)는 호환되는 조건에서 생성된 데이터를 입력받고 추정값뿐만 아니라 관련 불확실성과 적용 가능성(applicability)에 대한 정보도 반환해야 한다. 모델의 가정을 제외하고 인과 모델만 배포하면 사용자가 조건부 예측을 보편적인 인과적 결론으로 잘못 해석할 수 있다.

인과 메커니즘은 변화할 수 있으므로 배포 이후에도 모니터링(monitoring)을 계속해야 한다. 하드웨어 열화(hardware degradation), 새로운 모집단, 환경 변화, 정책 수정, 소프트웨어 업데이트 또는 인간 행동 변화는 이전까지 안정적이었던 관계를 무효화할 수 있다. 따라서 모니터링에서는 입력 분포(input distribution), 인과 잔차(causal residual), 개입 결과, 메커니즘 안정성(mechanism stability), 불확실성 및 예상된 구조적 관계의 위반 여부를 추적해야 한다.

예상하지 못한 결과(unexpected outcome)는 모델 수정에 매우 가치 있는 증거를 제공한다. 관측된 결과가 인과 예측과 일치하지 않을 경우 시스템은 문제가 측정 오류, 분포 변화(distribution shift), 잘못된 구조적 간선, 부정확한 메커니즘 또는 이전에 알려지지 않았던 숨겨진 변수에서 발생했는지를 판단해야 한다. 이러한 실패 사례는 추가 조사를 위한 표적 사례(targeted example)로 데이터 및 모델링 파이프라인에 다시 전달될 수 있다.

인과 모델에는 학습된 매개변수 이상이 포함되기 때문에 버전 관리(versioning)가 특히 중요하다. 완전한 버전에는 데이터셋, 변수 스키마(variable schema), 그래프 토폴로지(graph topology), 구조적 가정, 전처리 로직, 개입 정의, 추정 방법, 검증 결과, 불확실성 설정이 포함되어야 한다. 이를 통해 인과적 결론을 재현하고 두 모델 버전이 서로 다른 인과적 권고를 생성하는 이유를 추적할 수 있다.

영향력이 큰 응용 분야에서는 인간 검토(human review)가 여전히 중요하다. 전문가는 발견된 관계가 물리적으로, 운영적으로 또는 과학적으로 타당한지를 검토하고 알고리즘이 데이터만으로 확인할 수 없는 가정을 식별할 수 있다. 인간의 판단이 실증적 검증(empirical validation)을 대체해서는 안 되지만, 통계적으로는 매력적이지만 실제로 불가능한 인과 구조가 곧바로 운영 의사결정 시스템으로 전달되는 것을 방지할 수 있다.

피지컬 인공지능(Physical AI)에서 인과 모델 파이프라인은 데이터 인프라(data infrastructure)와 자율 지능(autonomous intelligence) 사이에서 지속적으로 작동할 수 있다. 다중 모달 경험(multimodal experience)은 관측을 제공하고, 로봇 행동은 개입을 제공하며, 인과 발견은 후보 메커니즘을 식별하고, 구조 모델은 결과를 예측하며, 플래너(planner)는 대안적인 행동을 평가한다. 이후 실제 배포는 현재의 인과 모델을 확인하고, 반박하거나, 개선할 수 있는 새로운 상호작용 데이터를 생성한다.

따라서 전체 파이프라인은 인과 질문을 정의하고, 의미 있는 변수를 구성하고, 구조를 제안하며, 관계를 발견하고, 개입 효과를 추정하고, 메커니즘을 검증하고, 모델을 배포하고, 결과를 관측하며, 가정을 수정하는 폐쇄형 인과 학습 순환(closed causal learning cycle)을 형성한다. 그 목적은 단순히 일반적으로 무엇이 발생하는지를 예측하는 것이 아니라, 사건이 왜 발생하며 의도적인 행동이 미래 결과를 어떻게 변화시킬 수 있는지에 대한 점점 더 신뢰성 높은 모델을 구축하는 것이다.

##  

## 07.03. Experimentation A B Testing [w/Code]

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Experimentation provides one of the strongest foundations for causal inference because it deliberately changes a variable and observes the resulting consequences. Unlike observational analysis, where treatment assignment may be influenced by hidden factors, a properly designed experiment controls how interventions are assigned. This makes it possible to estimate whether changing an action, policy, model, interface, or system parameter actually causes a measurable difference in an outcome.

A/B testing is the simplest and most widely used form of randomized controlled experimentation. Participants, devices, sessions, robots, environments, or other experimental units are assigned to alternative conditions, commonly called A and B. Condition A usually represents a baseline or existing system, while condition B introduces a specific intervention whose causal effect is being evaluated against that baseline.

Randomization is the central mechanism that gives A/B testing its causal interpretation. When experimental units are randomly assigned, observed and unobserved characteristics tend to become balanced between groups as sample size increases. Differences in outcomes can therefore be attributed more confidently to the intervention rather than systematic differences in the populations receiving each treatment.

Every experiment should begin with a clearly formulated causal hypothesis. The intervention, target population, primary outcome, expected direction of change, measurement window, and decision criterion should be specified before examining results. A hypothesis such as "the new planning policy reduces average task completion time" is more useful than the vague objective of determining whether the new policy performs better.

Experimental units must be selected carefully because the unit of randomization determines the statistical structure of the experiment. A unit may represent a user, robot, vehicle, production line, geographic region, episode, or time interval. Randomizing individual observations when multiple observations originate from the same underlying unit can underestimate uncertainty because those measurements may not be statistically independent.

Treatment and control conditions should differ primarily in the factor whose causal effect is being investigated. If several important components change simultaneously, an observed improvement cannot easily be attributed to one mechanism. Controlled experimentation therefore attempts to isolate interventions whenever practical, while factorial designs can be used when interactions among multiple factors are themselves important research questions.

Outcome metrics must be defined before experimentation begins. A primary metric represents the main causal objective, while secondary metrics provide additional information about system behavior. Guardrail metrics monitor undesirable side effects such as increased latency, energy consumption, failures, safety violations, customer complaints, or computational cost. Improvement in one metric should not conceal unacceptable degradation elsewhere.

Baseline measurement provides context for interpreting experimental effects. Historical performance, pre-intervention observations, or control-group statistics can reveal natural variability and help determine whether the expected effect is practically meaningful. Baselines are particularly valuable in engineering systems where environmental conditions, workloads, hardware states, and operating contexts can create substantial variation even without an intervention.

Sample-size planning determines whether an experiment has sufficient statistical power to detect an effect of meaningful magnitude. Required sample size depends on baseline variability, minimum detectable effect, significance threshold, desired power, and experimental design. Experiments with insufficient data may fail to detect real improvements, while extremely large experiments can make operationally irrelevant differences appear statistically significant.

The treatment effect can be estimated by comparing outcomes between experimental groups. In a simple randomized experiment, the difference between average outcomes provides an estimate of the average treatment effect. More sophisticated estimators can incorporate covariates, stratification, repeated measurements, heterogeneous effects, or sequential structure while preserving the logic established by randomized treatment assignment.

Statistical significance quantifies how compatible the observed difference is with a specified null hypothesis, but it should not be confused with practical importance. A very small effect may become statistically significant with enough samples while providing little engineering or business value. Experimental interpretation should therefore report effect magnitude, uncertainty intervals, operational relevance, and statistical evidence together.

Confidence intervals provide more information than a binary significant-or-not-significant decision. They indicate a range of effect values consistent with the observed data under the assumptions of the analysis. A wide interval signals substantial uncertainty, whereas a narrow interval indicates greater precision. Decision makers can compare this uncertainty with the minimum effect required to justify deployment.

Multiple testing requires careful management when many metrics, treatments, subgroups, or hypotheses are evaluated simultaneously. Repeatedly searching for statistically significant results increases the probability of false discoveries. Experiments should distinguish predefined hypotheses from exploratory analyses and, where necessary, apply appropriate corrections or hierarchical testing procedures to control error rates.

Sequential experimentation introduces additional considerations because results may be monitored while data is still accumulating. Repeatedly checking conventional significance tests and stopping as soon as a favorable result appears can inflate false-positive rates. Sequential testing methods, predefined stopping rules, or Bayesian approaches can support continuous monitoring while maintaining interpretable decision criteria.

A/A testing can be used before an important A/B experiment to verify that the experimentation infrastructure itself behaves correctly. Two groups receive effectively identical treatment, so persistent differences may reveal randomization problems, logging inconsistencies, metric bugs, sample-ratio mismatches, or hidden segmentation. This helps validate the measurement pipeline before causal conclusions are drawn from real interventions.

Stratification and blocking can improve experimental efficiency when important sources of variation are known in advance. Robots might be grouped by hardware version, users by market, or environments by terrain type before treatment assignment. Randomization then occurs within these groups, improving balance and reducing variance while preserving the experimental basis for causal inference.

Cluster randomized experiments are necessary when treatment naturally operates on groups rather than independent individuals. A policy may be deployed to an entire factory, fleet, site, classroom, or geographic region. Because observations within the same cluster can influence one another, analysis must account for intra-cluster dependence rather than incorrectly treating every observation as an independent experimental unit.

Interference becomes important when the treatment assigned to one unit affects the outcome of another. This violates the common assumption that each unit\'s outcome depends only on its own treatment. Network systems, multi-robot fleets, marketplaces, traffic systems, and social platforms frequently exhibit interference. Experimental design must therefore consider interactions among units when estimating causal effects.

Heterogeneous treatment effects reveal that an intervention may not affect every context equally. A new controller might improve performance on smooth terrain but degrade it on loose surfaces, while a model update may benefit familiar environments more than novel ones. Subgroup analysis can identify such differences, but hypotheses should preferably be defined before experimentation to reduce misleading post-hoc discoveries.

Contextual information should therefore accompany experimental records. Environment, hardware configuration, software version, workload, weather, sensor quality, task difficulty, operator behavior, and other relevant variables can help explain variations in treatment effects. These variables also support later causal generalization by showing where an experimentally validated mechanism remains stable and where it changes.

Experimentation pipelines should integrate closely with data and model pipelines. Assignment decisions, intervention parameters, timestamps, outcomes, context, model versions, and failures must be logged consistently. Reproducible records allow researchers to reconstruct exactly which system produced each observation and prevent experimental data from becoming disconnected from the conditions under which it was generated.

Online experiments evaluate interventions directly within deployed systems. They provide realistic evidence because treatment operates under actual workloads and environmental conditions, but they also introduce operational risks. Progressive rollout, canary deployment, exposure limits, monitoring, rollback mechanisms, and safety constraints can reduce these risks while still allowing causal evidence to accumulate.

Offline experimentation can complement online testing when direct intervention is expensive or dangerous. Simulators, digital twins, historical replay, laboratory environments, and hardware-in-the-loop systems can evaluate candidate changes before real-world exposure. These experiments provide useful screening evidence, although simulation results should not automatically be treated as equivalent to randomized evidence from the target environment.

For Physical AI, experimentation can evaluate perception models, localization algorithms, planning policies, control parameters, sensor configurations, energy strategies, and human-robot interaction methods. Experimental units may be robots, missions, trajectories, sites, or repeated scenarios. Physical constraints make careful design particularly important because uncontrolled variation in terrain, payload, battery state, and weather can obscure treatment effects.

Safety-critical experimentation requires additional restrictions because unrestricted randomization may expose systems or humans to unacceptable hazards. Candidate interventions can first pass simulation, offline evaluation, constrained environments, and safety verification before limited physical deployment. The experimental objective is therefore not simply to maximize statistical information but to acquire useful causal evidence while respecting operational safety boundaries.

Experiment results should ultimately feed back into causal models and decision systems. Successful interventions provide direct evidence about action-effect relationships, while failed experiments can reveal incorrect assumptions, hidden variables, or environment-dependent mechanisms. Experimental evidence can update causal graphs, structural models, world models, policies, and uncertainty estimates, creating a connection between scientific experimentation and autonomous learning.

A mature experimentation system forms a continuous cycle of hypothesis, intervention, measurement, causal estimation, validation, decision, deployment, and renewed experimentation. A/B testing provides a practical entry point into this cycle, but the broader objective is systematic causal learning. By designing interventions deliberately and measuring their consequences rigorously, AI and engineering systems can progress from observing correlations toward understanding which changes actually produce better outcomes.

실험(Experimentation)은 변수를 의도적으로 변화시키고 그 결과를 관측하기 때문에 인과 추론(causal inference)을 위한 가장 강력한 기반 가운데 하나를 제공한다. 처치 할당(treatment assignment)이 숨겨진 요인의 영향을 받을 수 있는 관측 분석(observational analysis)과 달리, 적절하게 설계된 실험은 개입(intervention)이 어떻게 할당되는지를 통제한다. 이를 통해 행동, 정책, 모델, 인터페이스 또는 시스템 매개변수의 변화가 실제로 결과에 측정 가능한 차이를 발생시키는지를 추정할 수 있다.

A/B 테스트(A/B Testing)는 가장 단순하면서도 널리 사용되는 무작위 통제 실험(randomized controlled experimentation)의 형태이다. 참가자, 장치, 세션, 로봇, 환경 또는 기타 실험 단위(experimental unit)를 일반적으로 A와 B라고 부르는 서로 다른 조건에 할당한다. 조건 A는 보통 기준선(baseline) 또는 기존 시스템을 나타내며, 조건 B는 해당 기준선과 비교하여 인과 효과를 평가하려는 특정 개입을 적용한다.

무작위화(randomization)는 A/B 테스트에 인과적 해석을 가능하게 하는 핵심 메커니즘이다. 실험 단위를 무작위로 할당하면 표본 크기가 증가함에 따라 관측된 특성과 관측되지 않은 특성이 집단 사이에서 균형을 이루는 경향이 있다. 따라서 결과의 차이를 각 처치를 받은 집단 사이의 체계적인 차이보다 개입 자체에 의해 발생한 것으로 더욱 신뢰성 있게 해석할 수 있다.

모든 실험은 명확하게 정의된 인과 가설(causal hypothesis)에서 시작해야 한다. 결과를 확인하기 전에 개입, 대상 모집단(target population), 주요 결과(primary outcome), 예상되는 변화 방향, 측정 기간(measurement window), 의사결정 기준을 정의해야 한다. "새로운 계획 정책이 평균 작업 완료 시간을 감소시킨다"와 같은 가설은 단순히 새로운 정책의 성능이 더 좋은지를 확인한다는 모호한 목표보다 훨씬 유용하다.

무작위화 단위(unit of randomization)가 실험의 통계적 구조를 결정하기 때문에 실험 단위를 신중하게 선택해야 한다. 하나의 단위는 사용자, 로봇, 차량, 생산 라인, 지리적 지역, 에피소드(episode), 시간 구간 등을 나타낼 수 있다. 동일한 기반 단위에서 여러 관측값이 발생하는데도 개별 관측을 각각 무작위화하면 이러한 측정값이 통계적으로 독립적이지 않을 수 있기 때문에 불확실성을 과소평가할 수 있다.

처치 조건(treatment condition)과 통제 조건(control condition)은 인과 효과를 조사하려는 요인을 중심으로 차이가 나도록 설계해야 한다. 여러 중요한 구성 요소를 동시에 변경하면 관측된 개선이 어떤 하나의 메커니즘 때문인지 쉽게 판단할 수 없다. 따라서 통제 실험(controlled experimentation)은 가능한 경우 개입을 분리하며, 여러 요인 사이의 상호작용 자체가 중요한 연구 질문이라면 요인 설계(factorial design)를 사용할 수 있다.

결과 지표(outcome metric)는 실험을 시작하기 전에 정의해야 한다. 주요 지표(primary metric)는 핵심적인 인과 목표를 나타내며, 보조 지표(secondary metric)는 시스템 동작에 대한 추가 정보를 제공한다. 가드레일 지표(guardrail metric)는 지연 시간 증가, 에너지 소비, 고장, 안전 위반, 고객 불만, 계산 비용과 같은 바람직하지 않은 부작용을 감시한다. 하나의 지표가 개선되었다는 이유로 다른 영역의 허용할 수 없는 성능 저하가 가려져서는 안 된다.

기준선 측정(baseline measurement)은 실험 효과를 해석하기 위한 맥락을 제공한다. 과거 성능, 개입 이전의 관측 또는 통제 집단 통계는 자연적인 변동성을 보여주고 예상되는 효과가 실제로 의미 있는지를 판단하는 데 도움을 준다. 기준선은 환경 조건, 작업 부하, 하드웨어 상태, 운영 맥락이 개입 없이도 상당한 변동을 발생시킬 수 있는 엔지니어링 시스템에서 특히 중요하다.

표본 크기 계획(sample-size planning)은 실험이 의미 있는 크기의 효과를 탐지할 수 있을 정도의 충분한 통계적 검정력(statistical power)을 가지는지를 결정한다. 필요한 표본 크기는 기준선 변동성, 최소 탐지 효과(minimum detectable effect), 유의 수준(significance threshold), 원하는 검정력 및 실험 설계에 따라 달라진다. 데이터가 부족하면 실제 개선을 발견하지 못할 수 있고, 지나치게 큰 실험에서는 운영적으로 의미 없는 차이가 통계적으로 유의하게 나타날 수 있다.

처치 효과(treatment effect)는 실험 집단 사이의 결과를 비교하여 추정할 수 있다. 단순한 무작위 실험에서는 집단별 평균 결과의 차이가 평균 처치 효과(Average Treatment Effect, ATE)의 추정값을 제공한다. 보다 정교한 추정 방법은 무작위 처치 할당을 통해 확보된 인과 추론의 논리를 유지하면서 공변량(covariate), 층화(stratification), 반복 측정, 이질적 효과(heterogeneous effect), 순차 구조(sequential structure)를 포함할 수 있다.

통계적 유의성(statistical significance)은 관측된 차이가 특정 귀무가설(null hypothesis)과 얼마나 양립할 수 있는지를 정량화하지만, 이를 실질적인 중요성(practical importance)과 혼동해서는 안 된다. 매우 작은 효과도 충분한 표본이 있으면 통계적으로 유의해질 수 있지만 공학적 또는 사업적 가치는 거의 없을 수 있다. 따라서 실험 해석에서는 효과 크기(effect magnitude), 불확실성 구간, 운영적 중요성 및 통계적 증거를 함께 보고해야 한다.

신뢰 구간(confidence interval)은 단순히 통계적으로 유의한지 아닌지를 판단하는 이진 결정(binary decision)보다 더 많은 정보를 제공한다. 신뢰 구간은 분석의 가정 아래에서 관측된 데이터와 일치하는 효과 값의 범위를 나타낸다. 넓은 구간은 상당한 불확실성을 의미하고, 좁은 구간은 더 높은 정밀도를 의미한다. 의사결정자는 이러한 불확실성을 실제 배포를 정당화하기 위해 필요한 최소 효과와 비교할 수 있다.

여러 지표, 처치, 하위 집단 또는 가설을 동시에 평가하는 경우 다중 검정(multiple testing)을 신중하게 관리해야 한다. 통계적으로 유의한 결과를 반복적으로 탐색하면 거짓 발견(false discovery)이 발생할 가능성이 높아진다. 따라서 실험에서는 사전에 정의된 가설과 탐색적 분석(exploratory analysis)을 구별해야 하며, 필요한 경우 오류율을 통제하기 위한 적절한 보정 방법이나 계층적 검정 절차(hierarchical testing procedure)를 적용해야 한다.

순차 실험(sequential experimentation)은 데이터가 계속 축적되는 동안 결과를 모니터링할 수 있기 때문에 추가적인 고려가 필요하다. 기존의 유의성 검정을 반복적으로 확인하고 유리한 결과가 나타나는 즉시 실험을 중단하면 거짓 양성률(false-positive rate)이 증가할 수 있다. 순차 검정(sequential testing), 사전에 정의된 중단 규칙(stopping rule), 베이지안 접근법(Bayesian approach)을 이용하면 해석 가능한 의사결정 기준을 유지하면서 지속적인 모니터링을 수행할 수 있다.

중요한 A/B 실험을 수행하기 전에 A/A 테스트(A/A Testing)를 이용하여 실험 인프라 자체가 올바르게 동작하는지를 검증할 수 있다. 두 집단에 사실상 동일한 처치를 제공하므로 지속적인 차이가 발견된다면 무작위화 문제, 로깅 불일치(logging inconsistency), 지표 오류(metric bug), 표본 비율 불일치(sample-ratio mismatch), 숨겨진 세분화(hidden segmentation) 등이 존재할 가능성이 있다. 이를 통해 실제 개입에서 인과적 결론을 도출하기 전에 측정 파이프라인을 검증할 수 있다.

중요한 변동 원인을 사전에 알고 있다면 층화(stratification)와 블로킹(blocking)을 이용하여 실험 효율성을 높일 수 있다. 예를 들어 로봇은 하드웨어 버전에 따라, 사용자는 시장에 따라, 환경은 지형 유형에 따라 그룹화할 수 있다. 이후 각 그룹 내부에서 무작위화를 수행하면 실험의 인과 추론 기반을 유지하면서 집단 간 균형을 향상시키고 분산(variance)을 감소시킬 수 있다.

처치가 독립적인 개체가 아니라 집단 단위로 적용되는 경우 군집 무작위 실험(cluster randomized experiment)이 필요하다. 하나의 정책이 전체 공장, 차량군(fleet), 사업장, 교실 또는 지리적 지역에 배포될 수 있다. 동일한 군집 내부의 관측값들은 서로 영향을 받을 수 있기 때문에 모든 관측을 독립적인 실험 단위로 잘못 취급해서는 안 되며, 분석 과정에서 군집 내 의존성(intra-cluster dependence)을 고려해야 한다.

하나의 실험 단위에 할당된 처치가 다른 실험 단위의 결과에 영향을 미치는 경우 간섭(interference)이 중요해진다. 이는 각 단위의 결과가 자신의 처치에만 의존한다는 일반적인 가정을 위반한다. 네트워크 시스템, 다중 로봇 플릿(multi-robot fleet), 마켓플레이스, 교통 시스템 및 소셜 플랫폼에서는 이러한 간섭이 빈번하게 발생한다. 따라서 인과 효과를 추정할 때 실험 설계 단계에서 실험 단위 사이의 상호작용을 고려해야 한다.

이질적 처치 효과(heterogeneous treatment effect)는 하나의 개입이 모든 상황에 동일한 영향을 주지 않을 수 있음을 보여준다. 새로운 제어기(controller)가 평탄한 지형에서는 성능을 향상시키지만 느슨한 노면에서는 성능을 저하시킬 수 있으며, 모델 업데이트가 새로운 환경보다 익숙한 환경에서 더 큰 효과를 보일 수도 있다. 하위 집단 분석(subgroup analysis)을 통해 이러한 차이를 발견할 수 있지만, 사후적으로 만들어진 잘못된 결론을 줄이기 위해 가능하면 실험 전에 가설을 정의하는 것이 바람직하다.

따라서 실험 기록에는 맥락 정보(contextual information)가 함께 포함되어야 한다. 환경, 하드웨어 구성, 소프트웨어 버전, 작업 부하, 날씨, 센서 품질, 작업 난이도, 운영자 행동 및 기타 관련 변수는 처치 효과가 달라지는 이유를 설명하는 데 도움을 줄 수 있다. 또한 이러한 변수는 실험적으로 검증된 메커니즘이 어떤 환경에서는 안정적으로 유지되고 어떤 환경에서는 변화하는지를 보여줌으로써 이후의 인과 일반화(causal generalization)를 지원한다.

실험 파이프라인(experimentation pipeline)은 데이터 파이프라인(data pipeline) 및 모델 파이프라인(model pipeline)과 긴밀하게 통합되어야 한다. 할당 결정, 개입 매개변수, 타임스탬프, 결과, 맥락, 모델 버전 및 실패 정보를 일관되게 기록해야 한다. 재현 가능한 기록을 통해 연구자는 어떤 시스템이 각각의 관측을 생성했는지를 정확하게 재구성할 수 있으며, 실험 데이터가 생성 당시의 조건과 분리되는 것을 방지할 수 있다.

온라인 실험(online experiment)은 실제 배포된 시스템 내부에서 직접 개입을 평가한다. 처치가 실제 작업 부하와 환경 조건에서 작동하기 때문에 현실적인 증거를 제공하지만 운영상의 위험도 발생시킨다. 점진적 롤아웃(progressive rollout), 카나리 배포(canary deployment), 노출 제한(exposure limit), 모니터링, 롤백(rollback) 메커니즘, 안전 제약을 이용하면 인과적 증거를 축적하면서 이러한 위험을 줄일 수 있다.

직접적인 개입에 높은 비용이나 위험이 존재하는 경우 오프라인 실험(offline experimentation)이 온라인 테스트를 보완할 수 있다. 시뮬레이터(simulator), 디지털 트윈(digital twin), 과거 데이터 재생(historical replay), 실험실 환경, 하드웨어 인 더 루프(Hardware-in-the-Loop, HIL) 시스템을 이용하여 실제 환경에 노출하기 전에 후보 변경 사항을 평가할 수 있다. 이러한 실험은 유용한 사전 검증 증거를 제공하지만 시뮬레이션 결과를 목표 환경에서 수행한 무작위 실험의 증거와 자동으로 동일하게 취급해서는 안 된다.

피지컬 인공지능(Physical AI)에서는 실험을 통해 인지 모델(perception model), 위치 추정 알고리즘(localization algorithm), 계획 정책(planning policy), 제어 매개변수, 센서 구성, 에너지 전략, 인간-로봇 상호작용(Human-Robot Interaction, HRI) 방법 등을 평가할 수 있다. 실험 단위는 로봇, 임무, 궤적, 장소 또는 반복 시나리오가 될 수 있다. 지형, 페이로드(payload), 배터리 상태, 날씨와 같은 통제되지 않은 변동이 처치 효과를 가릴 수 있으므로 물리적 시스템에서는 신중한 실험 설계가 특히 중요하다.

안전 필수 실험(safety-critical experimentation)에서는 제한 없는 무작위화가 시스템이나 인간을 허용할 수 없는 위험에 노출시킬 수 있기 때문에 추가적인 제한이 필요하다. 후보 개입은 제한적인 물리적 배포 전에 시뮬레이션, 오프라인 평가, 통제 환경 및 안전 검증(safety verification)을 먼저 통과할 수 있다. 따라서 실험의 목적은 단순히 통계적 정보를 최대화하는 것이 아니라 운영 안전 경계(operational safety boundary)를 준수하면서 유용한 인과적 증거를 확보하는 것이다.

실험 결과는 궁극적으로 인과 모델(causal model)과 의사결정 시스템으로 다시 전달되어야 한다. 성공적인 개입은 행동-효과 관계(action-effect relationship)에 대한 직접적인 증거를 제공하며, 실패한 실험은 잘못된 가정, 숨겨진 변수 또는 환경에 의존하는 메커니즘을 드러낼 수 있다. 실험 증거는 인과 그래프(causal graph), 구조 모델(structural model), 월드 모델(world model), 정책(policy), 불확실성 추정치를 갱신하여 과학적 실험과 자율 학습(autonomous learning)을 연결할 수 있다.

성숙한 실험 시스템은 가설(hypothesis), 개입, 측정(measurement), 인과 추정(causal estimation), 검증(validation), 의사결정(decision), 배포(deployment), 재실험으로 이어지는 지속적인 순환 구조를 형성한다. A/B 테스트는 이러한 순환 구조에 진입하는 실용적인 방법이지만 더 넓은 목적은 체계적인 인과 학습(systematic causal learning)에 있다. 개입을 의도적으로 설계하고 그 결과를 엄밀하게 측정함으로써 인공지능과 엔지니어링 시스템은 단순한 상관관계의 관측을 넘어 어떤 변화가 실제로 더 나은 결과를 만들어내는지를 이해하는 방향으로 발전할 수 있다.

##  

## 07.04. Causal Evaluation

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Causal evaluation determines whether a model has learned relationships that remain valid under intervention, environmental change, and alternative conditions rather than merely fitting correlations in observed data. Conventional evaluation often measures prediction accuracy on held-out samples, but a causal model can predict well while representing the underlying mechanism incorrectly. Causal evaluation therefore examines whether the model supports reliable reasoning about what changes outcomes and why.

A first requirement is to distinguish predictive performance from causal validity. A model may accurately estimate Y from X because X is strongly correlated with Y, even when X has no direct causal influence. Evaluation must therefore test whether changing X produces the predicted change in Y under controlled conditions. This shift from association to intervention is fundamental because causal claims concern consequences of deliberate change rather than ordinary co-occurrence.

Intervention-effect evaluation provides one of the strongest tests. A model predicts the outcome of a controlled intervention, and the prediction is compared with observations collected after that intervention is actually performed. Randomized experiments are especially valuable because assignment mechanisms reduce confounding. When direct experimentation is impossible, natural experiments, policy changes, or carefully designed quasi-experimental settings can provide weaker but still informative evidence.

Average treatment effect evaluation examines whether a model correctly estimates the average consequence of an intervention over a population. Depending on the application, evaluation may also examine conditional or individual treatment effects because interventions can influence different subgroups differently. A model that predicts the overall average correctly may still fail if it systematically misrepresents effects for particular environments, devices, users, or operating conditions.

Counterfactual evaluation is more difficult because only one factual outcome is normally observed for each event. The alternative outcome under a different intervention is inherently unobserved. Evaluation therefore relies on simulated environments with known mechanisms, paired experimental designs, repeated controlled conditions, synthetic benchmarks, or specially constructed datasets where counterfactual consistency can be assessed indirectly.

Causal graph evaluation compares discovered structural relationships with known or trusted causal structure when such ground truth exists. Metrics may assess whether the model identifies correct edges, directions, ancestors, intervention targets, or equivalence classes. Structural Hamming distance and precision-recall style measures can quantify graph recovery, but graph similarity alone does not guarantee that estimated intervention effects are accurate enough for practical decisions.

Edge orientation deserves separate attention because discovering that two variables are related is easier than determining causal direction. Evaluation should distinguish adjacency recovery from direction recovery. A graph containing the correct variables but reversed causal arrows may generate good observational predictions while producing incorrect intervention recommendations. Directional accuracy is therefore especially important for decision-support and autonomous-control systems.

Mechanism evaluation examines whether the learned structural equations or causal transition functions behave correctly. Instead of testing only whether the graph topology is plausible, the evaluator asks whether each learned mechanism produces realistic outputs when its causal parents change. This is particularly important in nonlinear systems where the correct graph may still contain inaccurate functional relationships.

Invariance across environments provides another central evaluation criterion. Stable causal mechanisms should often remain valid when unrelated distributions change. Models can therefore be evaluated across different sites, populations, sensor configurations, lighting conditions, terrains, workloads, policies, or time periods. A causal model should preserve correct intervention relationships even when superficial statistical associations shift.

Out-of-distribution evaluation extends this principle to unfamiliar conditions. The model is tested on environments deliberately chosen to differ from training data. Performance under such shifts reveals whether the model has learned transferable mechanisms or relied on environment-specific shortcuts. Causal generalization should ideally degrade gracefully when only irrelevant factors change and adapt selectively when a genuine mechanism changes.

Confounding robustness evaluates whether causal conclusions survive the presence of variables that influence both treatment and outcome. Synthetic benchmarks can introduce controlled confounders, while real-world evaluation can compare adjusted estimates against randomized or experimentally validated effects. Hidden confounding remains particularly challenging, so sensitivity analysis should quantify how strong an unobserved confounder would need to be to overturn the conclusion.

Sensitivity analysis tests dependence on assumptions rather than data alone. Evaluators can vary adjustment sets, model classes, graph constraints, prior knowledge, noise assumptions, intervention strength, or measurement error. If small reasonable changes produce large differences in estimated effects, the result is fragile. Robust conclusions should remain broadly stable across a defensible range of modeling assumptions.

Calibration is important because causal models often report uncertainty as well as point estimates. A well-calibrated model should express greater uncertainty when evidence is weak, interventions are unfamiliar, or multiple causal graphs remain plausible. Confidence intervals, posterior distributions, or prediction sets can be evaluated for coverage and sharpness, ensuring that confidence statements correspond reasonably well to observed error frequencies.

Uncertainty in causal structure should be evaluated separately from uncertainty in mechanism parameters. Multiple graphs may fit the observational data equally well, creating structural ambiguity even when parameters within each graph are estimated precisely. Evaluation can examine ensembles, posterior graph probabilities, or equivalence classes to determine whether the system appropriately represents unresolved causal structure rather than collapsing prematurely to one explanation.

Temporal causal evaluation must test both direction and delay. A system may correctly identify that X influences Y but incorrectly estimate when the effect occurs. Lag recovery, impulse responses, delayed intervention effects, feedback dynamics, and long-horizon propagation should therefore be tested. This is especially important in control systems, robotics, industrial processes, and other environments where timing directly affects decision quality.

Multimodal causal evaluation should test whether causal conclusions remain consistent across different sensing channels. If vision, LiDAR, audio, force, and proprioception provide evidence about the same physical mechanism, the model should connect them through a coherent latent state. Evaluation can intentionally remove, corrupt, or delay modalities to determine whether the causal representation remains stable under sensor failure or partial observability.

Counterfactual consistency across modalities provides an especially demanding test. If a hypothetical action changes an object\'s motion, predicted visual, geometric, inertial, and force observations should change in mutually compatible ways. Independent modality predictors may generate individually plausible outputs that conflict physically. A causal multimodal model should instead produce alternative futures that remain consistent with one underlying world state.

Decision quality is ultimately one of the most important evaluation criteria. A causal model may recover an elegant graph yet provide little practical value if its recommendations are poor. Evaluators can measure whether intervention selection, policy optimization, planning, diagnosis, or resource allocation improves when the causal model is used. This connects structural correctness with downstream operational consequences.

Regret-based evaluation can quantify the cost of choosing actions based on an inaccurate causal model. If the model recommends intervention A when intervention B would have produced a substantially better outcome, the difference represents decision regret. This perspective is useful for comparing models that have similar statistical fit but different consequences when integrated into planning and control systems.

Safety evaluation should examine whether causal errors create hazardous actions. Models may be tested on rare failures, unstable states, extreme environmental conditions, sensor faults, and adversarial distribution shifts. A safety-critical causal system should identify uncertainty and abstain or fall back to conservative behavior when its causal assumptions are no longer well supported rather than confidently applying invalid mechanisms.

Experimental reproducibility is also part of evaluation. Causal results should be reproducible from the same data, code, variable definitions, graph assumptions, preprocessing steps, and intervention specifications. Versioned evaluation artifacts make it possible to determine whether changes in conclusions originate from new evidence, altered assumptions, software modifications, or stochastic training variation.

Benchmark design requires careful attention because conventional random train-test splits can exaggerate causal performance. Strong benchmarks should separate environments, interventions, temporal regimes, objects, subjects, devices, or sites. They should include distribution shifts and mechanism changes intentionally, allowing evaluators to distinguish interpolation ability from genuine causal transfer and adaptation.

Synthetic benchmarks remain valuable because the true causal graph and intervention effects are known exactly. Researchers can systematically vary graph size, noise, hidden confounding, nonlinear mechanisms, missing variables, feedback, and sample size. However, synthetic success does not guarantee real-world validity because generated systems may be much cleaner than operational environments.

Semi-synthetic evaluation provides a middle ground by combining real covariates or sensor distributions with simulated treatment mechanisms and outcomes. This preserves realistic complexity while retaining known causal ground truth. Such benchmarks can test whether algorithms recover effects under realistic high-dimensional inputs, although conclusions still depend on how faithfully the synthetic causal mechanism represents actual applications.

Real-world evaluation provides the strongest operational evidence but usually the weakest access to complete causal ground truth. Controlled deployments, randomized trials, repeated interventions, laboratory systems, and carefully instrumented robotic experiments can provide partial truth. Evaluation should therefore combine multiple forms of evidence rather than relying on a single score that implies more certainty than the available data supports.

For Physical AI, causal evaluation should include closed-loop testing. Perception estimates the current state, the causal model predicts action consequences, planning selects interventions, control executes them, and new observations reveal whether the predicted mechanism was correct. Evaluation can measure trajectory outcomes, intervention accuracy, adaptation speed, safety violations, energy use, recovery behavior, and model updates across repeated interactions.

World-model evaluation should similarly move beyond next-frame or next-state prediction. A causal world model should be tested on unseen actions, counterfactual trajectories, mechanism changes, novel object combinations, sensor degradation, and environmental shifts. Planning success under these conditions provides stronger evidence than reconstruction accuracy alone because it requires the model to support intervention-aware simulation.

Continuous evaluation is necessary after deployment because causal validity can decay. New environments, software versions, hardware wear, policy changes, human adaptation, or sensor replacements may alter mechanisms. Monitoring should therefore track causal residuals, intervention outcomes, uncertainty, environment coverage, and mechanism stability, triggering revalidation when evidence suggests that previously trusted relationships have changed.

Causal evaluation ultimately asks whether an AI system understands enough of the underlying mechanism to make reliable decisions when the world changes. Strong evaluation combines structural tests, intervention experiments, counterfactual checks, uncertainty calibration, environmental shifts, and downstream decision outcomes. The goal is not merely to certify that a model predicts well, but to determine whether its causal claims remain useful, robust, and safe when they are used to change real systems.

인과 평가(Causal Evaluation)는 모델이 관측 데이터에서 단순히 상관관계(correlation)를 적합한 것이 아니라 개입(intervention), 환경 변화(environmental change), 대안적 조건(alternative condition)에서도 유효하게 유지되는 관계를 학습했는지를 판단한다. 일반적인 평가는 별도로 분리된 표본에서 예측 정확도(prediction accuracy)를 측정하지만, 인과 모델은 기반 메커니즘을 잘못 표현하면서도 높은 예측 성능을 보일 수 있다. 따라서 인과 평가는 무엇이 결과를 변화시키며 왜 그러한 변화가 발생하는지에 대해 모델이 신뢰할 수 있는 추론을 지원하는지를 검토한다.

첫 번째 요구사항은 예측 성능(predictive performance)과 인과적 타당성(causal validity)을 구별하는 것이다. 모델은 X가 Y와 강한 상관관계를 가지고 있기 때문에 X로부터 Y를 정확하게 추정할 수 있지만, 실제로는 X가 Y에 직접적인 인과 영향을 미치지 않을 수도 있다. 따라서 평가에서는 통제된 조건에서 X를 변화시켰을 때 Y가 모델이 예측한 방향으로 변화하는지를 검증해야 한다. 연관성에서 개입으로의 이러한 전환은 인과적 주장이 일반적인 동시 발생이 아니라 의도적인 변화의 결과를 다룬다는 점에서 핵심적이다.

개입 효과 평가(intervention-effect evaluation)는 가장 강력한 검증 방법 가운데 하나를 제공한다. 모델이 통제된 개입의 결과를 예측하고, 해당 개입을 실제로 수행한 이후 수집된 관측 결과와 예측을 비교한다. 무작위 실험(randomized experiment)은 할당 메커니즘(assignment mechanism)이 교란(confounding)을 감소시키기 때문에 특히 중요하다. 직접적인 실험이 불가능하다면 자연 실험(natural experiment), 정책 변화 또는 신중하게 설계된 준실험(quasi-experimental setting)을 통해 상대적으로 약하지만 여전히 유용한 증거를 얻을 수 있다.

평균 처치 효과 평가(Average Treatment Effect Evaluation)는 모델이 모집단 전체에서 개입의 평균적인 결과를 올바르게 추정하는지를 검토한다. 응용 분야에 따라 개입이 서로 다른 하위 집단에 다르게 영향을 줄 수 있으므로 조건부 처치 효과(conditional treatment effect) 또는 개별 처치 효과(individual treatment effect)도 평가할 수 있다. 전체 평균을 정확하게 예측하는 모델이라도 특정 환경, 장치, 사용자 또는 운영 조건에 대한 효과를 체계적으로 잘못 표현할 수 있다.

반사실적 평가(counterfactual evaluation)는 각 사건에서 일반적으로 하나의 사실적 결과(factual outcome)만 관측할 수 있기 때문에 더욱 어렵다. 다른 개입이 이루어졌을 경우의 대안적 결과는 본질적으로 관측되지 않는다. 따라서 알려진 메커니즘을 가진 시뮬레이션 환경, 쌍을 이루는 실험 설계(paired experimental design), 반복적인 통제 조건, 합성 벤치마크(synthetic benchmark), 또는 반사실적 일관성을 간접적으로 평가할 수 있도록 특별히 구성된 데이터셋을 활용해야 한다.

인과 그래프 평가(causal graph evaluation)는 실제 또는 신뢰할 수 있는 인과 구조가 존재하는 경우 발견된 구조적 관계를 해당 기준과 비교한다. 평가 지표는 모델이 올바른 간선(edge), 방향(direction), 선행 원인(ancestor), 개입 대상(intervention target), 동치 클래스(equivalence class)를 식별하는지를 측정할 수 있다. 구조적 해밍 거리(Structural Hamming Distance)와 정밀도-재현율(precision-recall) 계열의 지표는 그래프 복원 정도를 정량화할 수 있지만, 그래프의 유사성만으로 추정된 개입 효과가 실제 의사결정에 충분히 정확하다는 것을 보장하지는 않는다.

간선 방향(edge orientation)은 별도로 주의 깊게 평가해야 한다. 두 변수가 서로 관련되어 있다는 사실을 발견하는 것은 인과 방향을 결정하는 것보다 상대적으로 쉽다. 따라서 평가는 인접 관계 복원(adjacency recovery)과 방향 복원(direction recovery)을 구별해야 한다. 올바른 변수들을 포함하고 있더라도 인과 화살표가 반대로 설정된 그래프는 관측 데이터에서는 좋은 예측을 제공하면서 개입에 대해서는 잘못된 권고를 생성할 수 있다. 따라서 방향 정확도(directional accuracy)는 의사결정 지원 및 자율 제어 시스템에서 특히 중요하다.

메커니즘 평가(mechanism evaluation)는 학습된 구조 방정식(structural equation) 또는 인과 전이 함수(causal transition function)가 올바르게 동작하는지를 검토한다. 단순히 그래프 토폴로지(graph topology)가 타당한지를 검사하는 것에서 나아가 인과 부모(causal parent)가 변화할 때 각각의 학습된 메커니즘이 현실적인 출력을 생성하는지를 평가한다. 이는 올바른 그래프를 가지고 있더라도 내부 함수 관계가 부정확할 수 있는 비선형 시스템에서 특히 중요하다.

환경 간 불변성(invariance across environments)은 또 다른 핵심 평가 기준을 제공한다. 안정적인 인과 메커니즘은 관련되지 않은 분포가 변화하더라도 유지되는 경우가 많다. 따라서 서로 다른 장소, 모집단, 센서 구성, 조명 조건, 지형, 작업 부하, 정책 또는 시간 구간에서 모델을 평가할 수 있다. 인과 모델은 표면적인 통계적 연관성이 변화하더라도 올바른 개입 관계를 유지해야 한다.

분포 외 평가(out-of-distribution evaluation)는 이러한 원리를 익숙하지 않은 조건까지 확장한다. 모델은 훈련 데이터와 의도적으로 다른 환경에서 테스트된다. 이러한 변화에서의 성능은 모델이 전이 가능한 메커니즘(transferable mechanism)을 학습했는지 아니면 환경에 특화된 지름길(shortcut)에 의존했는지를 보여준다. 이상적으로 인과 일반화(causal generalization)는 관련 없는 요인만 변화할 경우 성능이 안정적으로 유지되어야 하며, 실제 메커니즘이 변화할 경우에는 선택적으로 적응해야 한다.

교란 강건성(confounding robustness)은 처치와 결과 모두에 영향을 주는 변수가 존재하더라도 인과적 결론이 유지되는지를 평가한다. 합성 벤치마크에서는 통제된 교란 요인을 도입할 수 있으며, 실제 환경에서는 조정된 추정값(adjusted estimate)을 무작위 실험이나 실험적으로 검증된 효과와 비교할 수 있다. 숨겨진 교란(hidden confounding)은 특히 어렵기 때문에 민감도 분석(sensitivity analysis)을 통해 관측되지 않은 교란 요인이 어느 정도 강해야 기존 결론을 뒤집을 수 있는지를 정량화해야 한다.

민감도 분석은 데이터뿐만 아니라 가정(assumption)에 대한 결과의 의존성을 검증한다. 평가자는 조정 집합(adjustment set), 모델 클래스, 그래프 제약, 사전 지식(prior knowledge), 잡음 가정, 개입 강도 또는 측정 오류를 변화시킬 수 있다. 합리적인 범위의 작은 변화가 추정 효과에 큰 차이를 발생시킨다면 해당 결과는 취약한 것으로 판단해야 한다. 반대로 방어 가능한 가정 범위에서 대체로 안정적으로 유지되는 결론은 더 높은 강건성을 가진다.

인과 모델은 점 추정값(point estimate)뿐만 아니라 불확실성(uncertainty)을 함께 제공하는 경우가 많기 때문에 보정(calibration)이 중요하다. 잘 보정된 모델은 증거가 부족하거나 개입이 익숙하지 않거나 여러 인과 그래프가 가능한 경우 더 높은 불확실성을 표현해야 한다. 신뢰 구간(confidence interval), 사후 분포(posterior distribution), 예측 집합(prediction set)의 포함률(coverage)과 정밀도(sharpness)를 평가하여 모델이 표현하는 신뢰도가 실제 오류 빈도와 합리적으로 일치하는지를 확인할 수 있다.

인과 구조의 불확실성(causal structure uncertainty)은 메커니즘 매개변수의 불확실성과 별도로 평가해야 한다. 여러 그래프가 관측 데이터를 동일하게 잘 설명할 수 있기 때문에 각 그래프 내부의 매개변수가 정밀하게 추정되더라도 구조적인 모호성(structural ambiguity)이 존재할 수 있다. 평가에서는 앙상블(ensemble), 사후 그래프 확률(posterior graph probability), 동치 클래스를 검토하여 시스템이 해결되지 않은 인과 구조를 성급하게 하나의 설명으로 확정하지 않고 적절하게 표현하는지를 판단할 수 있다.

시간 인과 평가(temporal causal evaluation)는 인과 방향뿐만 아니라 시간 지연(delay)도 검증해야 한다. 시스템은 X가 Y에 영향을 준다는 사실은 올바르게 식별하면서 그 효과가 언제 발생하는지는 잘못 추정할 수 있다. 따라서 지연 복원(lag recovery), 임펄스 응답(impulse response), 지연된 개입 효과(delayed intervention effect), 피드백 동역학(feedback dynamics), 장기 전파(long-horizon propagation)를 평가해야 한다. 이는 시간 정보가 의사결정 품질에 직접적인 영향을 미치는 제어 시스템, 로보틱스, 산업 공정에서 특히 중요하다.

다중 모달 인과 평가(multimodal causal evaluation)는 서로 다른 센싱 채널에서도 인과적 결론이 일관되게 유지되는지를 검증해야 한다. 비전, 라이다(LiDAR), 오디오, 힘, 고유수용감각(proprioception)이 동일한 물리적 메커니즘에 대한 증거를 제공한다면 모델은 이들을 일관된 잠재 상태(latent state)를 통해 연결해야 한다. 특정 모달리티(modality)를 의도적으로 제거하거나 손상시키거나 지연시켜 센서 고장이나 부분 관측 상황에서도 인과 표현이 안정적으로 유지되는지를 평가할 수 있다.

모달리티 사이의 반사실적 일관성(counterfactual consistency)은 특히 까다로운 평가를 제공한다. 가상의 행동으로 객체의 운동이 변화한다면 예측된 시각, 기하학, 관성 및 힘 관측도 서로 일치하는 방향으로 변화해야 한다. 독립적인 모달리티 예측기는 각각 그럴듯한 결과를 생성하면서도 물리적으로 서로 모순될 수 있다. 반면 인과 다중 모달 모델(causal multimodal model)은 하나의 기반 세계 상태(underlying world state)와 일치하는 대안적 미래를 생성해야 한다.

의사결정 품질(decision quality)은 궁극적으로 가장 중요한 평가 기준 가운데 하나이다. 인과 모델이 정교한 그래프를 복원하더라도 권고하는 행동이 좋지 않다면 실질적인 가치는 제한된다. 따라서 인과 모델을 사용할 때 개입 선택(intervention selection), 정책 최적화(policy optimization), 계획(planning), 진단(diagnosis), 자원 할당(resource allocation)이 실제로 향상되는지를 측정할 수 있다. 이는 구조적 정확성을 실제 운영 결과와 연결한다.

후회 기반 평가(regret-based evaluation)는 부정확한 인과 모델을 기반으로 행동을 선택했을 때 발생하는 비용을 정량화할 수 있다. 모델이 개입 A를 권고했지만 개입 B가 훨씬 더 좋은 결과를 만들어냈다면 그 차이를 의사결정 후회(decision regret)로 볼 수 있다. 이러한 관점은 통계적 적합도가 비슷하지만 계획 및 제어 시스템에 통합되었을 때 서로 다른 결과를 만들어내는 모델들을 비교하는 데 유용하다.

안전 평가(safety evaluation)는 인과적 오류가 위험한 행동을 만들어내는지를 검토해야 한다. 모델은 희귀 고장, 불안정 상태, 극단적인 환경 조건, 센서 오류, 적대적 분포 변화(adversarial distribution shift) 등을 대상으로 평가할 수 있다. 안전 필수 인과 시스템(safety-critical causal system)은 인과적 가정이 더 이상 충분히 뒷받침되지 않을 경우 잘못된 메커니즘을 확신을 가지고 적용하기보다 불확실성을 식별하고 행동을 보류하거나 보수적인 동작으로 전환해야 한다.

실험 재현성(experimental reproducibility) 역시 평가의 일부이다. 인과 결과는 동일한 데이터, 코드, 변수 정의, 그래프 가정, 전처리 단계, 개입 명세(intervention specification)를 사용했을 때 재현할 수 있어야 한다. 버전 관리된 평가 산출물(versioned evaluation artifact)을 통해 결론의 변화가 새로운 증거, 변경된 가정, 소프트웨어 수정 또는 확률적 학습 변동 중 무엇에서 발생했는지를 확인할 수 있다.

벤치마크 설계(benchmark design)는 일반적인 무작위 훈련-테스트 분할(random train-test split)이 인과 성능을 과대평가할 수 있기 때문에 세심한 주의가 필요하다. 강력한 벤치마크는 환경, 개입, 시간 영역, 객체, 피험자, 장치 또는 장소를 분리해야 한다. 또한 분포 변화와 메커니즘 변화를 의도적으로 포함하여 단순한 보간 능력(interpolation ability)과 실제 인과 전이(causal transfer) 및 적응 능력을 구별할 수 있어야 한다.

합성 벤치마크(synthetic benchmark)는 실제 인과 그래프와 개입 효과를 정확하게 알고 있기 때문에 여전히 가치가 높다. 연구자는 그래프 크기, 잡음, 숨겨진 교란, 비선형 메커니즘, 누락 변수, 피드백, 표본 크기를 체계적으로 변화시킬 수 있다. 그러나 생성된 시스템은 실제 운영 환경보다 훨씬 단순하고 깨끗할 수 있기 때문에 합성 데이터에서의 성공이 실제 환경에서의 타당성을 보장하지는 않는다.

반합성 평가(semi-synthetic evaluation)는 실제 공변량(covariate) 또는 센서 분포와 시뮬레이션된 처치 메커니즘 및 결과를 결합하여 중간적인 접근법을 제공한다. 이를 통해 현실적인 복잡성을 유지하면서 알려진 인과 정답(causal ground truth)을 확보할 수 있다. 이러한 벤치마크는 현실적인 고차원 입력에서 알고리즘이 인과 효과를 복원할 수 있는지를 검증할 수 있지만, 결론은 합성된 인과 메커니즘이 실제 응용 환경을 얼마나 충실하게 표현하는지에 여전히 의존한다.

실제 환경 평가(real-world evaluation)는 가장 강력한 운영적 증거를 제공하지만 완전한 인과 정답에 접근하기는 일반적으로 가장 어렵다. 통제된 배포(controlled deployment), 무작위 시험(randomized trial), 반복적인 개입, 실험실 시스템, 정밀하게 계측된 로봇 실험을 통해 부분적인 정답을 확보할 수 있다. 따라서 평가는 사용 가능한 데이터가 실제로 제공하는 것보다 더 높은 확실성을 암시하는 하나의 점수에 의존하지 않고 여러 형태의 증거를 결합해야 한다.

피지컬 인공지능(Physical AI)의 인과 평가에는 폐루프 테스트(closed-loop testing)가 포함되어야 한다. 지각(perception)은 현재 상태를 추정하고, 인과 모델은 행동의 결과를 예측하며, 계획(planning)은 개입을 선택하고, 제어(control)는 이를 실행하며, 새로운 관측을 통해 예측된 메커니즘이 올바른지를 판단한다. 평가는 반복적인 상호작용 과정에서 궤적 결과, 개입 정확도, 적응 속도, 안전 위반, 에너지 사용량, 복구 행동(recovery behavior), 모델 갱신 등을 측정할 수 있다.

월드 모델 평가(world-model evaluation) 역시 다음 프레임 또는 다음 상태 예측만을 넘어야 한다. 인과 월드 모델(causal world model)은 경험하지 않은 행동, 반사실적 궤적(counterfactual trajectory), 메커니즘 변화, 새로운 객체 조합, 센서 성능 저하, 환경 변화에 대해 평가해야 한다. 이러한 조건에서의 계획 성공(planning success)은 단순한 재구성 정확도(reconstruction accuracy)보다 더 강력한 증거를 제공하는데, 이는 모델이 개입을 고려한 시뮬레이션(intervention-aware simulation)을 지원해야 하기 때문이다.

인과적 타당성은 시간이 지나면서 저하될 수 있기 때문에 배포 이후에도 지속적 평가(continuous evaluation)가 필요하다. 새로운 환경, 소프트웨어 버전, 하드웨어 마모, 정책 변화, 인간의 적응, 센서 교체는 기존 메커니즘을 변화시킬 수 있다. 따라서 모니터링은 인과 잔차(causal residual), 개입 결과, 불확실성, 환경 커버리지(environment coverage), 메커니즘 안정성(mechanism stability)을 추적하고, 이전에 신뢰했던 관계가 변화했다는 증거가 나타날 경우 재검증(revalidation)을 수행해야 한다.

궁극적으로 인과 평가(Causal Evaluation)는 인공지능 시스템이 세계가 변화할 때에도 신뢰할 수 있는 의사결정을 내릴 수 있을 정도로 기반 메커니즘을 이해하고 있는지를 묻는다. 강력한 평가는 구조적 검증(structural test), 개입 실험(intervention experiment), 반사실적 검증(counterfactual check), 불확실성 보정(uncertainty calibration), 환경 변화, 실제 의사결정 결과를 결합한다. 목표는 단순히 모델이 정확하게 예측한다는 사실을 확인하는 것이 아니라, 실제 시스템을 변화시키는 데 인과적 주장을 사용할 때에도 그것이 유용하고 강건하며 안전하게 유지되는지를 판단하는 것이다.

##  

## 07.05. Integration with AI Systems

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Integration with AI systems connects causal modeling with the broader computational architecture responsible for perception, prediction, reasoning, planning, learning, and action. A causal component should not operate as an isolated analytical module. Its value emerges when causal variables, intervention effects, structural assumptions, and uncertainty estimates become usable information for other AI components that must understand situations and make decisions.

Modern AI architectures frequently contain several specialized models rather than one monolithic intelligence. Perception models interpret raw sensory inputs, representation models construct latent states, predictive models estimate future conditions, causal models describe mechanisms, planners evaluate possible actions, and control systems execute decisions. Integration requires clearly defined interfaces so that information can move consistently between these components.

The integration process begins by establishing a shared representation of system state. Perception outputs such as detected objects, semantic features, trajectories, forces, language concepts, or environmental conditions must be mapped into variables understood by the causal model. Conversely, causal predictions must be translated into representations that downstream planning and decision modules can consume without losing their meaning or associated uncertainty.

Causal representation learning can provide an important bridge between high-dimensional perception and symbolic or structured reasoning. Instead of treating every latent feature as an arbitrary statistical dimension, the system attempts to organize representations around meaningful factors such as objects, properties, actions, interactions, and mechanisms. These variables can then support intervention-aware prediction while remaining connected to neural perception pipelines.

Integration with deep learning allows causal systems to operate on complex sensory information. Neural networks can extract useful representations from images, video, point clouds, audio, language, and multimodal streams, while causal structures constrain how selected representations interact. This creates hybrid architectures in which deep learning handles high-dimensional approximation and causal modeling provides explicit structure for reasoning about changes and consequences.

Predictive models and causal models serve complementary purposes. Predictive models efficiently estimate what is likely to happen under familiar conditions, whereas causal models attempt to determine how outcomes change when actions or mechanisms are modified. An integrated system can therefore use predictive inference for routine operation and invoke more explicit causal reasoning when evaluating interventions, unfamiliar situations, failures, or strategic decisions.

World models provide a natural architecture for integrating causal knowledge. A conventional world model predicts how latent states evolve over time, while a causal world model represents actions as interventions on transition mechanisms. This allows the system to distinguish passive environmental evolution from changes deliberately produced by an agent and provides a stronger foundation for internal simulation and planning.

In sequential systems, the current state can be inferred from multimodal observations and passed to a causal transition model. Candidate actions are then applied as hypothetical interventions, producing alternative future trajectories. A planner can compare these trajectories according to objectives, constraints, uncertainty, and safety requirements. The selected action is executed, and the resulting observation provides new evidence about whether the assumed causal mechanism was correct.

Reinforcement learning can benefit from this intervention-oriented structure. Standard reinforcement learning often learns action policies from correlations among states, actions, rewards, and transitions. Causal reinforcement learning attempts to identify which aspects of the environment actually determine action outcomes. This knowledge can improve exploration, transfer, sample efficiency, and robustness when the environment changes from the conditions encountered during training.

Model-based reinforcement learning offers an especially direct integration path. The causal model can function as part of the learned dynamics model used to simulate future states. Instead of generating trajectories solely from statistical transition patterns, the agent can reason about how interventions modify specific mechanisms. Planning can then compare actions under alternative assumptions and avoid relying excessively on correlations that may disappear outside the training distribution.

Large language models can also interact with causal systems. Language models provide broad semantic knowledge, flexible interfaces, task decomposition, and natural-language reasoning, while explicit causal models can supply structured information about intervention effects and system mechanisms. The language model can formulate causal questions or interpret results, but numerical or safety-critical causal conclusions should remain grounded in validated models and evidence.

Retrieval-augmented generation can further connect causal reasoning with external knowledge. Technical documents, experiment records, system logs, causal graphs, and previous intervention results can be retrieved according to the current task. The retrieved evidence can provide context for causal hypotheses while the causal model evaluates structural relationships. This combination separates knowledge retrieval from claims about what interventions actually produce specific outcomes.

AI agents extend integration from inference to autonomous task execution. An agent may observe its environment, maintain memory, formulate goals, retrieve knowledge, construct hypotheses, select tools, plan interventions, execute actions, and evaluate results. A causal model can support this loop by predicting action consequences and identifying which additional observations or experiments would most reduce uncertainty about the current problem.

Memory systems are important because causal knowledge accumulates across interactions. Episodic memory can preserve previous situations, actions, and outcomes, while semantic memory can store generalized mechanisms and relationships. Experimental evidence should remain distinguishable from ordinary observations. This enables an agent to retrieve not merely similar experiences but evidence about which actions previously changed outcomes under comparable conditions.

Planning systems can use causal graphs to reduce the action search space. If the desired outcome depends on a limited set of upstream variables, the planner can prioritize interventions that influence those variables rather than evaluating every available action. Structural knowledge can therefore improve computational efficiency while also providing explanations for why a particular action sequence is expected to achieve the target state.

Hierarchical planning can combine causal reasoning at multiple levels of abstraction. High-level reasoning determines goals, subgoals, and relevant mechanisms, while lower-level models handle trajectories and control commands. For example, a causal planner may determine that reducing wheel slip requires changing velocity or traction conditions, while a motion controller determines the precise actuator commands needed to implement that intervention.

Control systems require causal reasoning to operate within strict temporal constraints. Fast feedback loops may not permit expensive graph inference or counterfactual simulation at every cycle. A practical architecture can therefore separate slower causal reasoning from high-frequency control. Causal models establish constraints, references, or policy adjustments, while optimized controllers execute them at the rates required by the physical system.

Uncertainty must be propagated across integrated AI modules. A perception system may be uncertain about an object\'s identity, the causal model may be uncertain about the relevant mechanism, and the planner may face uncertainty about future outcomes. If each component reports only its most likely estimate, downstream systems can become unjustifiably confident. Interfaces should therefore preserve uncertainty whenever it materially affects decisions.

Safety architectures can use causal information to evaluate whether proposed actions might trigger hazardous mechanisms. Before execution, candidate actions can be checked against structural constraints, predicted consequences, safety envelopes, or known failure pathways. When causal uncertainty becomes too high, the system can reject the proposed intervention, request additional information, reduce operating speed, or transition to a conservative fallback policy.

Digital twins provide another important integration environment. A digital twin can combine physical models, learned dynamics, operational data, and causal mechanisms to represent a real system. AI components can test interventions within the twin before applying them physically. Differences between simulated and observed outcomes then become evidence for updating model parameters, causal assumptions, or representations of environmental conditions.

Simulation and generative models can expand the range of situations available for causal reasoning. Generative models can produce candidate environments, object configurations, trajectories, or sensory observations, while causal constraints determine whether generated alternatives remain mechanically or logically consistent. This combination can support counterfactual simulation, rare-event generation, and systematic exploration of conditions that are difficult to collect physically.

Multimodal AI requires causal relationships to remain coherent across sensory representations. An object collision may simultaneously produce visual motion, geometric displacement, acoustic signals, force changes, and inertial responses. Integrated causal models should represent these observations as consequences of a shared event rather than unrelated correlations. This supports more robust inference when one sensor becomes noisy, delayed, or unavailable.

Deployment architecture determines where causal computation occurs. Lightweight causal checks may execute on edge devices, while computationally intensive discovery, large-scale simulation, or model updates may run on on-premise servers or cloud infrastructure. The architecture should account for latency, bandwidth, privacy, reliability, compute capacity, and safety requirements rather than assuming every causal function belongs at the same computational layer.

Model serving requires stable interfaces and explicit version control. Each causal service should define expected variables, units, temporal assumptions, supported interventions, output semantics, uncertainty measures, and applicability conditions. The causal graph, structural equations, preprocessing logic, and model parameters should be versioned together because changing any of these components can alter the meaning of downstream decisions.

Monitoring should examine interactions among AI components rather than evaluating each model independently. A perception update can change causal variables, a causal-model update can alter planner behavior, and a new planning policy can change the distribution of collected data. System-level monitoring must therefore detect interface drift, incompatible versions, unexpected feedback loops, distribution changes, and deteriorating closed-loop performance.

For Physical AI, integration ultimately creates a continuous perception-causality-planning-action-learning cycle. Sensors observe the physical world, perception constructs state representations, causal models estimate mechanisms and intervention effects, world models simulate possible futures, planners choose actions, controllers execute them, and resulting observations return as new evidence. Each interaction can therefore improve both task performance and understanding of the environment.

The long-term objective is an AI architecture in which causal reasoning becomes a functional layer connecting learning with deliberate action. Statistical learning identifies patterns, causal modeling organizes mechanisms, world models predict alternative futures, agents formulate interventions, and control systems act on the physical world. Their integration enables AI systems to move beyond recognizing what usually happens toward reasoning about why it happens, what could happen differently, and which actions can reliably produce desired outcomes.

인공지능 시스템과의 통합(Integration with AI Systems)은 인과 모델링(causal modeling)을 지각(perception), 예측(prediction), 추론(reasoning), 계획(planning), 학습(learning), 행동(action)을 담당하는 보다 광범위한 계산 아키텍처(computational architecture)와 연결한다. 인과 구성 요소(causal component)는 독립적인 분석 모듈로 동작해서는 안 된다. 인과 변수(causal variable), 개입 효과(intervention effect), 구조적 가정(structural assumption), 불확실성 추정(uncertainty estimate)이 상황을 이해하고 의사결정을 내려야 하는 다른 인공지능 구성 요소에서 활용 가능한 정보가 될 때 그 가치가 나타난다.

현대 인공지능 아키텍처는 하나의 단일 지능(monolithic intelligence)보다는 여러 개의 전문화된 모델을 포함하는 경우가 많다. 지각 모델(perception model)은 원시 감각 입력을 해석하고, 표현 모델(representation model)은 잠재 상태(latent state)를 구성하며, 예측 모델(predictive model)은 미래 상태를 추정하고, 인과 모델(causal model)은 메커니즘을 설명하며, 플래너(planner)는 가능한 행동을 평가하고, 제어 시스템(control system)은 의사결정을 실행한다. 통합을 위해서는 이러한 구성 요소 사이에서 정보가 일관되게 이동할 수 있도록 명확하게 정의된 인터페이스(interface)가 필요하다.

통합 과정은 시스템 상태(system state)에 대한 공유 표현(shared representation)을 확립하는 것에서 시작한다. 탐지된 객체, 의미 특징(semantic feature), 궤적(trajectory), 힘, 언어 개념, 환경 조건과 같은 지각 출력은 인과 모델이 이해할 수 있는 변수로 매핑되어야 한다. 반대로 인과 예측은 그 의미와 관련된 불확실성을 잃지 않으면서 후속 계획 및 의사결정 모듈이 사용할 수 있는 표현으로 변환되어야 한다.

인과 표현 학습(causal representation learning)은 고차원 지각(high-dimensional perception)과 기호적 또는 구조화된 추론(symbolic or structured reasoning) 사이의 중요한 연결 고리를 제공할 수 있다. 모든 잠재 특징을 임의적인 통계 차원으로 취급하는 대신 시스템은 객체, 속성, 행동, 상호작용, 메커니즘과 같은 의미 있는 요인을 중심으로 표현을 구성하려 한다. 이러한 변수는 신경망 기반 지각 파이프라인(neural perception pipeline)과 연결된 상태를 유지하면서 개입 인식 예측(intervention-aware prediction)을 지원할 수 있다.

딥러닝(deep learning)과의 통합을 통해 인과 시스템은 복잡한 감각 정보를 처리할 수 있다. 신경망(neural network)은 이미지, 비디오, 포인트 클라우드(point cloud), 오디오, 언어, 다중 모달 스트림(multimodal stream)으로부터 유용한 표현을 추출하고, 인과 구조는 선택된 표현들이 어떻게 상호작용하는지를 제약한다. 이를 통해 딥러닝이 고차원 근사(high-dimensional approximation)를 담당하고 인과 모델링이 변화와 결과를 추론하기 위한 명시적인 구조를 제공하는 하이브리드 아키텍처(hybrid architecture)를 구성할 수 있다.

예측 모델과 인과 모델은 상호 보완적인 목적을 가진다. 예측 모델은 익숙한 조건에서 무엇이 발생할 가능성이 높은지를 효율적으로 추정하는 반면, 인과 모델은 행동이나 메커니즘이 변경되었을 때 결과가 어떻게 달라지는지를 판단하려 한다. 따라서 통합 시스템은 일상적인 운영에는 예측 추론(predictive inference)을 사용하고, 개입, 익숙하지 않은 상황, 고장 또는 전략적 의사결정을 평가할 때 더욱 명시적인 인과 추론(causal reasoning)을 활용할 수 있다.

월드 모델(world model)은 인과 지식(causal knowledge)을 통합하기 위한 자연스러운 아키텍처를 제공한다. 일반적인 월드 모델은 잠재 상태가 시간에 따라 어떻게 변화하는지를 예측하지만, 인과 월드 모델(causal world model)은 행동을 전이 메커니즘(transition mechanism)에 대한 개입으로 표현한다. 이를 통해 시스템은 수동적인 환경 변화와 에이전트가 의도적으로 발생시킨 변화를 구별할 수 있으며, 내부 시뮬레이션(internal simulation)과 계획을 위한 더욱 강력한 기반을 확보할 수 있다.

순차 시스템(sequential system)에서는 다중 모달 관측으로부터 현재 상태를 추론하여 인과 전이 모델(causal transition model)에 전달할 수 있다. 이후 후보 행동(candidate action)을 가상의 개입(hypothetical intervention)으로 적용하여 서로 다른 미래 궤적을 생성한다. 플래너는 목표, 제약 조건, 불확실성, 안전 요구사항에 따라 이러한 궤적을 비교한다. 선택된 행동을 실행한 후 발생하는 관측은 가정했던 인과 메커니즘이 올바른지를 검증하는 새로운 증거가 된다.

강화학습(reinforcement learning)은 이러한 개입 중심 구조(intervention-oriented structure)의 이점을 활용할 수 있다. 일반적인 강화학습은 상태, 행동, 보상, 상태 전이 사이의 상관관계로부터 행동 정책(action policy)을 학습하는 경우가 많다. 인과 강화학습(causal reinforcement learning)은 환경의 어떤 요소가 실제로 행동 결과를 결정하는지를 식별하려 한다. 이러한 지식은 훈련에서 경험한 조건과 환경이 달라질 때 탐색(exploration), 전이(transfer), 표본 효율성(sample efficiency), 강건성(robustness)을 향상시킬 수 있다.

모델 기반 강화학습(Model-Based Reinforcement Learning)은 특히 직접적인 통합 경로를 제공한다. 인과 모델은 미래 상태를 시뮬레이션하는 데 사용되는 학습된 동역학 모델(learned dynamics model)의 일부로 기능할 수 있다. 단순히 통계적 상태 전이 패턴으로 궤적을 생성하는 대신 에이전트는 개입이 특정 메커니즘을 어떻게 변화시키는지를 추론할 수 있다. 계획은 서로 다른 가정 아래에서 행동을 비교하고 훈련 분포 밖에서 사라질 가능성이 있는 상관관계에 과도하게 의존하는 것을 방지할 수 있다.

대규모 언어 모델(Large Language Model, LLM) 역시 인과 시스템과 상호작용할 수 있다. 언어 모델은 폭넓은 의미 지식(semantic knowledge), 유연한 인터페이스, 작업 분해(task decomposition), 자연어 추론을 제공하고, 명시적 인과 모델은 개입 효과와 시스템 메커니즘에 대한 구조화된 정보를 제공할 수 있다. 언어 모델은 인과 질문을 구성하거나 결과를 해석할 수 있지만 수치적 또는 안전 필수 인과 결론(safety-critical causal conclusion)은 검증된 모델과 증거에 기반해야 한다.

검색 증강 생성(Retrieval-Augmented Generation, RAG)은 인과 추론을 외부 지식과 더욱 긴밀하게 연결할 수 있다. 기술 문서, 실험 기록, 시스템 로그, 인과 그래프, 이전 개입 결과를 현재 작업에 따라 검색할 수 있다. 검색된 증거는 인과 가설(causal hypothesis)을 위한 맥락을 제공하고 인과 모델은 구조적 관계를 평가할 수 있다. 이러한 결합은 지식 검색(knowledge retrieval)과 특정 개입이 실제로 어떤 결과를 발생시키는지에 관한 주장을 구분한다.

인공지능 에이전트(AI agent)는 추론에서 자율적인 작업 실행으로 통합 범위를 확장한다. 에이전트는 환경을 관측하고, 기억을 유지하고, 목표를 수립하고, 지식을 검색하고, 가설을 구성하고, 도구를 선택하고, 개입을 계획하고, 행동을 실행하고, 결과를 평가할 수 있다. 인과 모델은 행동의 결과를 예측하고 현재 문제에 대한 불확실성을 가장 크게 감소시킬 추가적인 관측이나 실험이 무엇인지를 식별함으로써 이러한 순환 과정을 지원할 수 있다.

인과 지식은 상호작용을 거치면서 축적되기 때문에 기억 시스템(memory system)이 중요하다. 일화 기억(episodic memory)은 이전 상황, 행동, 결과를 보존할 수 있고, 의미 기억(semantic memory)은 일반화된 메커니즘과 관계를 저장할 수 있다. 실험적 증거(experimental evidence)는 일반적인 관측과 구별되어야 한다. 이를 통해 에이전트는 단순히 유사한 경험을 검색하는 것을 넘어 유사한 조건에서 어떤 행동이 이전에 실제 결과를 변화시켰는지에 대한 증거를 검색할 수 있다.

계획 시스템(planning system)은 인과 그래프(causal graph)를 이용하여 행동 탐색 공간(action search space)을 줄일 수 있다. 원하는 결과가 제한된 수의 상위 원인 변수(upstream variable)에 의존한다면 플래너는 가능한 모든 행동을 평가하는 대신 해당 변수에 영향을 주는 개입을 우선적으로 검토할 수 있다. 따라서 구조적 지식(structural knowledge)은 계산 효율성을 향상시키는 동시에 특정 행동 시퀀스가 목표 상태를 달성할 것으로 예상되는 이유에 대한 설명을 제공할 수 있다.

계층적 계획(hierarchical planning)은 여러 추상화 수준에서 인과 추론을 결합할 수 있다. 상위 수준의 추론은 목표, 하위 목표(subgoal), 관련 메커니즘을 결정하고, 하위 수준 모델은 궤적과 제어 명령을 처리한다. 예를 들어 인과 플래너는 휠 슬립(wheel slip)을 줄이기 위해 속도나 접지 조건(traction condition)을 변화시켜야 한다고 판단하고, 모션 컨트롤러(motion controller)는 해당 개입을 구현하기 위해 필요한 정확한 액추에이터 명령(actuator command)을 결정할 수 있다.

제어 시스템은 엄격한 시간 제약 아래에서 동작하기 때문에 인과 추론을 적용할 때 이를 고려해야 한다. 빠른 피드백 루프(fast feedback loop)에서는 매 제어 주기마다 계산 비용이 높은 그래프 추론이나 반사실적 시뮬레이션(counterfactual simulation)을 수행하기 어려울 수 있다. 따라서 실용적인 아키텍처에서는 상대적으로 느린 인과 추론과 고주파 제어(high-frequency control)를 분리할 수 있다. 인과 모델은 제약, 기준값(reference), 정책 조정을 설정하고 최적화된 컨트롤러는 물리 시스템이 요구하는 속도로 이를 실행한다.

통합된 인공지능 모듈 사이에서는 불확실성(uncertainty)이 전파되어야 한다. 지각 시스템은 객체의 정체에 대해 불확실할 수 있고, 인과 모델은 관련 메커니즘에 대해 불확실할 수 있으며, 플래너는 미래 결과에 대한 불확실성을 가질 수 있다. 각각의 구성 요소가 가장 가능성이 높은 하나의 추정값만 전달하면 후속 시스템이 정당한 근거 없이 지나치게 높은 확신을 가질 수 있다. 따라서 의사결정에 실질적인 영향을 주는 경우 인터페이스는 불확실성을 보존해야 한다.

안전 아키텍처(safety architecture)는 인과 정보를 이용하여 제안된 행동이 위험한 메커니즘을 촉발할 가능성을 평가할 수 있다. 행동을 실행하기 전에 후보 행동을 구조적 제약(structural constraint), 예측된 결과, 안전 영역(safety envelope), 알려진 고장 경로(failure pathway)와 비교할 수 있다. 인과적 불확실성이 지나치게 높아지면 시스템은 제안된 개입을 거부하거나 추가 정보를 요청하고, 운행 속도를 낮추거나, 보수적인 대체 정책(conservative fallback policy)으로 전환할 수 있다.

디지털 트윈(digital twin)은 또 다른 중요한 통합 환경을 제공한다. 디지털 트윈은 물리 모델(physical model), 학습된 동역학, 운영 데이터, 인과 메커니즘을 결합하여 실제 시스템을 표현할 수 있다. 인공지능 구성 요소는 물리 시스템에 실제로 적용하기 전에 트윈 내부에서 개입을 테스트할 수 있다. 이후 시뮬레이션 결과와 실제 관측 결과의 차이는 모델 매개변수, 인과 가정 또는 환경 조건 표현을 갱신하기 위한 증거가 된다.

시뮬레이션(simulation)과 생성 모델(generative model)은 인과 추론에 사용할 수 있는 상황의 범위를 확장할 수 있다. 생성 모델은 후보 환경, 객체 구성, 궤적 또는 감각 관측을 생성할 수 있으며, 인과적 제약은 생성된 대안이 기계적으로 또는 논리적으로 일관성을 유지하는지를 결정한다. 이러한 결합은 반사실적 시뮬레이션, 희귀 사건 생성(rare-event generation), 실제 환경에서 수집하기 어려운 조건의 체계적인 탐색을 지원할 수 있다.

다중 모달 인공지능(multimodal AI)에서는 감각 표현 사이에서 인과관계가 일관성을 유지해야 한다. 객체 충돌은 시각적 운동, 기하학적 변위, 음향 신호, 힘의 변화, 관성 반응을 동시에 발생시킬 수 있다. 통합된 인과 모델은 이러한 관측을 서로 관련 없는 상관관계가 아니라 하나의 공유 사건(shared event)의 결과로 표현해야 한다. 이를 통해 하나의 센서가 잡음에 오염되거나 지연되거나 사용할 수 없게 되더라도 더욱 강건한 추론을 수행할 수 있다.

배포 아키텍처(deployment architecture)는 인과 계산이 어디에서 수행되는지를 결정한다. 경량 인과 검증(lightweight causal check)은 엣지 장치(edge device)에서 실행할 수 있는 반면, 계산 비용이 높은 인과 발견, 대규모 시뮬레이션 또는 모델 업데이트는 온프레미스 서버(on-premise server)나 클라우드 인프라(cloud infrastructure)에서 실행할 수 있다. 모든 인과 기능이 동일한 계산 계층에 존재한다고 가정하기보다 지연 시간, 대역폭, 개인정보 보호, 신뢰성, 계산 용량, 안전 요구사항을 고려하여 아키텍처를 설계해야 한다.

모델 서빙(model serving)을 위해서는 안정적인 인터페이스와 명시적인 버전 관리(version control)가 필요하다. 각각의 인과 서비스(causal service)는 예상 변수, 단위, 시간적 가정, 지원되는 개입, 출력 의미(output semantics), 불확실성 척도, 적용 가능 조건(applicability condition)을 정의해야 한다. 이러한 구성 요소 가운데 하나라도 변경되면 후속 의사결정의 의미가 달라질 수 있으므로 인과 그래프, 구조 방정식(structural equation), 전처리 로직, 모델 매개변수를 함께 버전 관리해야 한다.

모니터링(monitoring)은 각각의 모델을 독립적으로 평가하는 것을 넘어 인공지능 구성 요소 사이의 상호작용을 검토해야 한다. 지각 모델의 업데이트는 인과 변수를 변화시킬 수 있고, 인과 모델의 업데이트는 플래너의 행동을 변화시키며, 새로운 계획 정책은 다시 수집되는 데이터의 분포를 변화시킬 수 있다. 따라서 시스템 수준 모니터링(system-level monitoring)은 인터페이스 드리프트(interface drift), 호환되지 않는 버전, 예상하지 못한 피드백 루프, 분포 변화, 폐루프 성능(closed-loop performance)의 저하를 탐지해야 한다.

피지컬 인공지능(Physical AI)에서 이러한 통합은 궁극적으로 지속적인 지각-인과-계획-행동-학습 순환(perception-causality-planning-action-learning cycle)을 형성한다. 센서는 물리 세계를 관측하고, 지각 시스템은 상태 표현을 구성하며, 인과 모델은 메커니즘과 개입 효과를 추정하고, 월드 모델은 가능한 미래를 시뮬레이션하며, 플래너는 행동을 선택하고, 컨트롤러는 이를 실행한다. 그 결과로 발생하는 관측은 다시 새로운 증거로 돌아오며, 각각의 상호작용은 작업 성능뿐만 아니라 환경에 대한 이해를 향상시킬 수 있다.

장기적인 목표는 인과 추론(causal reasoning)이 학습과 의도적인 행동(deliberate action)을 연결하는 기능적 계층(functional layer)이 되는 인공지능 아키텍처를 구축하는 것이다. 통계적 학습(statistical learning)은 패턴을 식별하고, 인과 모델링은 메커니즘을 구조화하며, 월드 모델은 대안적인 미래를 예측하고, 에이전트는 개입을 구성하며, 제어 시스템은 물리 세계에서 행동한다. 이러한 요소들의 통합을 통해 인공지능 시스템은 일반적으로 무엇이 발생하는지를 인식하는 수준을 넘어 왜 그것이 발생하는지, 무엇이 다르게 발생할 수 있는지, 그리고 어떤 행동이 원하는 결과를 신뢰성 있게 만들어낼 수 있는지를 추론하는 방향으로 발전할 수 있다.

##  

## 07.06. MLOps for Causal AI

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

MLOps for Causal AI extends conventional machine learning operations beyond managing predictive models to managing causal assumptions, intervention logic, structural relationships, and evidence about mechanisms. A causal system can remain statistically accurate while its causal interpretation becomes invalid, so deployment infrastructure must monitor not only prediction quality but also whether the relationships used for interventions and decisions continue to hold.

Traditional MLOps organizes the lifecycle of data preparation, model training, validation, deployment, monitoring, and retraining. Causal AI adds another lifecycle around causal graphs, structural equations, adjustment sets, intervention definitions, assumptions, experiments, and counterfactual models. These artifacts must evolve together because changing one component can alter the meaning or validity of causal estimates produced by the entire system.

The causal data pipeline begins with rigorous definitions of variables and their roles. Treatment variables, outcomes, confounders, mediators, colliders, contextual variables, and intervention targets should be represented consistently across collection, storage, training, and serving. Metadata should preserve units, timestamps, sampling conditions, provenance, sensor configuration, experimental assignment, and whether each observation resulted from passive observation or deliberate intervention.

Data lineage becomes especially important because causal conclusions depend on how data was generated. Two datasets containing identical variables may support different conclusions if one originates from randomized intervention and another from observational behavior. Causal MLOps should therefore preserve data-generating context, treatment assignment mechanisms, inclusion criteria, environment information, and known selection processes rather than treating all records as interchangeable training samples.

Version control must extend beyond model parameters. Causal graphs, graph constraints, structural equations, prior knowledge, variable dictionaries, preprocessing logic, intervention specifications, identification strategies, estimators, and sensitivity assumptions should be versioned alongside code and datasets. A deployed causal estimate should be traceable to the exact combination of evidence and assumptions that produced it.

A causal model registry can complement the conventional model registry by storing structural information and applicability conditions. Each registered model should identify supported interventions, target populations, environments, required adjustment variables, expected temporal relationships, uncertainty methods, and known limitations. This prevents downstream systems from applying a causal model to situations for which its assumptions were never validated.

Training pipelines for causal AI may combine several computational stages. Representation learning can convert high-dimensional observations into candidate variables, causal discovery can propose structural relationships, identification determines whether desired effects can be estimated, and causal estimation quantifies those effects. These stages should be reproducible independently because an error in any one of them can propagate into later intervention decisions.

Automated causal discovery requires additional governance because discovered graphs are hypotheses rather than guaranteed truths. MLOps pipelines can compare newly learned structures against domain constraints, previous graph versions, experimental evidence, temporal ordering, and forbidden relationships. Large structural changes should trigger review rather than automatically replacing a trusted causal model solely because a new dataset favors a different graph.

Continuous integration for causal AI should test structural and statistical properties before models are merged or deployed. Automated tests can verify graph acyclicity where required, variable availability, temporal ordering, intervention compatibility, adjustment-set validity, estimator behavior, and expected responses on synthetic causal cases. Unit tests can also encode known mechanisms that should remain invariant across software changes.

Continuous delivery requires stronger deployment gates than ordinary predictive serving when causal outputs directly influence decisions. A candidate model can pass offline validation, simulation, shadow deployment, limited intervention testing, and controlled rollout before receiving full authority. The deployment pipeline should distinguish systems that merely display causal analysis from systems that automatically select or execute interventions.

Experiment management is a central component of causal MLOps. Randomized trials, A/B tests, controlled robotic experiments, simulation studies, and natural experiments should be connected to the model lifecycle. Experiment definitions, treatment assignments, outcomes, exclusions, stopping rules, and analysis plans should be stored systematically so that new causal evidence can update models without losing the context under which it was generated.

Observational and interventional datasets should remain distinguishable throughout the pipeline. Observational data can provide broad environmental coverage, while interventional data provides stronger evidence about specific mechanisms. Combining them can improve causal learning, but the training system must preserve which relationships are supported primarily by correlation and which have direct experimental evidence.

Validation pipelines should test more than held-out prediction accuracy. Causal models should be evaluated on intervention-effect accuracy, graph stability, counterfactual consistency, environmental invariance, uncertainty calibration, sensitivity to confounding, and downstream decision quality. Where possible, predicted intervention effects should be compared against randomized or controlled experimental outcomes rather than relying exclusively on observational validation.

Simulation provides an important validation layer before physical deployment. Synthetic environments, digital twins, and learned world models can generate interventions that would be expensive, rare, or unsafe to perform in reality. A causal model can be challenged with mechanism changes, sensor failures, distribution shifts, extreme states, and novel action combinations before it is allowed to influence a real operational system.

Deployment should preserve the causal context required by inference. A serving endpoint should not simply accept arbitrary feature vectors and return treatment effects. It should verify that required variables are available, values lie within supported ranges, the requested intervention is defined, and the current environment resembles conditions where the model was validated. Unsupported queries should produce uncertainty or rejection rather than unjustified estimates.

Causal model serving may expose several types of outputs. Services can provide intervention effects, counterfactual outcomes, causal pathways, recommended actions, uncertainty intervals, or warnings about violated assumptions. Interface contracts should specify exactly what each output means because downstream agents or planners may otherwise interpret a conditional prediction as an intervention effect and make incorrect decisions.

Monitoring causal AI requires separating data drift from mechanism drift. Data drift occurs when observed variable distributions change, while mechanism drift occurs when the causal relationship generating an outcome changes. A shift in appearance, weather, user population, or workload may not invalidate a causal mechanism, whereas hardware degradation, policy changes, new control logic, or altered physical dynamics can directly change the mechanism itself.

Causal residual monitoring can help detect such changes. After an intervention is executed, the observed outcome can be compared with the causal model\'s expected consequence. Persistent discrepancies may indicate parameter drift, structural change, hidden confounding, sensor problems, or an unsupported operating regime. Monitoring therefore converts real-world interventions into continuing evidence about whether deployed causal assumptions remain trustworthy.

Graph drift is another important monitoring target. Newly collected evidence may suggest that relationships among variables have changed or that previously stable dependencies no longer hold. Rather than automatically rebuilding the graph, the system can compare candidate structures with the deployed version and identify changed edges, orientations, mechanisms, or uncertainty. Significant structural drift should trigger investigation and revalidation.

Uncertainty should influence operational policies. A causal service can attach confidence intervals, posterior uncertainty, structural ambiguity, or applicability scores to its outputs. Downstream systems can use these signals to determine whether to execute an intervention, request additional observations, run a simulation, consult a human operator, or select a conservative fallback action. Uncertainty therefore becomes an operational control variable rather than merely a reporting statistic.

Rollback mechanisms are essential because causal errors can affect actions rather than only predictions. Every deployed causal model should have a recoverable previous version and clearly defined fallback behavior. If monitoring detects unexpected intervention outcomes, safety violations, severe drift, or interface incompatibility, the system should be able to restore a previously validated graph, estimator, policy, or rule-based controller.

For Physical AI, causal MLOps must connect software lifecycle management with hardware configuration. Robot mass, payload, tire condition, actuator characteristics, sensor placement, battery state, firmware, controller versions, and environmental conditions can alter physical mechanisms. Model metadata should therefore identify the hardware and operating envelope for which each causal model has been validated rather than assuming one model applies universally.

Edge deployment creates additional constraints because robots and autonomous devices require low latency and reliable operation even when network connectivity is limited. Lightweight causal inference, safety checks, and intervention evaluation may run locally, while causal discovery, large simulations, graph updates, and retraining occur on on-premise or cloud infrastructure. Synchronization mechanisms must ensure that edge models receive validated versions without disrupting active control.

Digital twins can serve as a staging environment between model development and physical deployment. Candidate causal models can first interact with a virtual representation of the robot, factory, vehicle, or process. Differences between predicted and simulated intervention outcomes reveal model weaknesses, while differences between the twin and physical system reveal simulation gaps. Both forms of error should be tracked separately within the lifecycle.

Integration with world models enables causal MLOps to manage predictive simulation as another versioned dependency. A causal planner may rely on a perception model, state representation, causal graph, dynamics model, reward function, and safety model simultaneously. Deployment records should capture this complete dependency set because changing the world model while leaving the causal graph unchanged can still alter resulting action decisions.

AI agents introduce another operational layer because causal outputs may become inputs to autonomous reasoning and tool use. Agent logs should record which causal query was made, which model version answered it, what evidence was retrieved, what intervention was selected, and what outcome followed. This creates an auditable chain from observation through causal reasoning to action and consequence.

Governance should distinguish learned evidence, domain assumptions, and human constraints. Some causal edges may be experimentally supported, others inferred statistically, and others imposed because of physical knowledge or safety requirements. Recording these categories allows reviewers to understand why a relationship exists in the deployed model and prevents automated retraining from silently removing constraints that were intentionally introduced.

Reproducibility requires packaging the entire causal analysis environment. Data snapshots, graph definitions, estimator settings, random seeds, software dependencies, experiment records, evaluation reports, and deployment configuration should be sufficient to reconstruct important causal results. Reproducibility becomes especially valuable when an intervention produces an unexpected outcome and engineers must determine exactly why the system made its decision.

A mature Causal AI MLOps platform therefore establishes a continuous loop connecting data, causal discovery, estimation, experimentation, validation, deployment, monitoring, and revision. New observations and interventions generate evidence, evidence updates mechanisms, updated mechanisms pass through validation gates, and validated models return to operation. This creates a disciplined process in which causal knowledge evolves without sacrificing traceability or safety.

The ultimate objective of MLOps for Causal AI is not merely to keep causal models running, but to keep causal decisions trustworthy as systems and environments evolve. By managing evidence, assumptions, graphs, interventions, uncertainty, experiments, hardware context, and deployment history as first-class operational artifacts, organizations can transform causal reasoning from a research capability into a reliable component of continuously operating AI systems.

인과 인공지능을 위한 MLOps(MLOps for Causal AI)는 일반적인 머신러닝 운영(machine learning operations)을 단순한 예측 모델 관리에서 인과적 가정(causal assumption), 개입 논리(intervention logic), 구조적 관계(structural relationship), 메커니즘에 대한 증거 관리까지 확장한다. 인과 시스템은 통계적 정확도를 유지하면서도 인과적 해석이 더 이상 유효하지 않을 수 있기 때문에, 배포 인프라는 예측 품질뿐만 아니라 개입과 의사결정에 사용되는 관계가 계속 유지되는지도 모니터링해야 한다.

일반적인 MLOps는 데이터 준비, 모델 학습, 검증(validation), 배포(deployment), 모니터링(monitoring), 재학습(retraining)의 생명주기(lifecycle)를 관리한다. 인과 인공지능(Causal AI)은 여기에 인과 그래프(causal graph), 구조 방정식(structural equation), 조정 집합(adjustment set), 개입 정의(intervention definition), 가정, 실험, 반사실적 모델(counterfactual model)의 생명주기를 추가한다. 이들 산출물(artifact)은 하나의 구성 요소가 변경되면 전체 시스템이 생성하는 인과 추정의 의미나 타당성이 달라질 수 있으므로 함께 진화해야 한다.

인과 데이터 파이프라인(causal data pipeline)은 변수와 그 역할을 엄밀하게 정의하는 것에서 시작한다. 처치 변수(treatment variable), 결과(outcome), 교란 요인(confounder), 매개 변수(mediator), 콜라이더(collider), 맥락 변수(contextual variable), 개입 대상(intervention target)을 데이터 수집, 저장, 학습, 서빙(serving) 전체에서 일관되게 표현해야 한다. 메타데이터(metadata)는 단위, 타임스탬프(timestamp), 샘플링 조건, 데이터 출처(provenance), 센서 구성, 실험 할당, 그리고 각각의 관측이 수동적 관측인지 의도적인 개입의 결과인지를 보존해야 한다.

데이터 계보(data lineage)는 인과적 결론이 데이터가 어떻게 생성되었는지에 의존하기 때문에 특히 중요하다. 동일한 변수를 포함하는 두 데이터셋이라도 하나가 무작위 개입(randomized intervention)에서 생성되고 다른 하나가 관측 행동(observational behavior)에서 생성되었다면 서로 다른 결론을 지원할 수 있다. 따라서 인과 MLOps는 모든 기록을 동일한 학습 샘플로 취급하지 않고 데이터 생성 맥락, 처치 할당 메커니즘, 포함 기준(inclusion criteria), 환경 정보, 알려진 선택 과정(selection process)을 보존해야 한다.

버전 관리(version control)는 모델 매개변수를 넘어 확장되어야 한다. 인과 그래프, 그래프 제약(graph constraint), 구조 방정식, 사전 지식(prior knowledge), 변수 사전(variable dictionary), 전처리 로직, 개입 명세(intervention specification), 식별 전략(identification strategy), 추정기(estimator), 민감도 가정(sensitivity assumption)을 코드 및 데이터셋과 함께 버전 관리해야 한다. 배포된 인과 추정값은 이를 생성한 정확한 증거와 가정의 조합까지 추적 가능해야 한다.

인과 모델 레지스트리(causal model registry)는 일반적인 모델 레지스트리(model registry)를 보완하여 구조적 정보와 적용 가능 조건(applicability condition)을 저장할 수 있다. 등록된 각 모델은 지원하는 개입, 대상 모집단(target population), 환경, 필요한 조정 변수, 예상되는 시간 관계, 불확실성 방법, 알려진 한계를 명시해야 한다. 이를 통해 후속 시스템이 검증되지 않은 상황에 인과 모델을 적용하는 것을 방지할 수 있다.

인과 인공지능을 위한 학습 파이프라인(training pipeline)은 여러 계산 단계를 결합할 수 있다. 표현 학습(representation learning)은 고차원 관측을 후보 변수로 변환하고, 인과 발견(causal discovery)은 구조적 관계를 제안하며, 식별(identification)은 원하는 효과를 추정할 수 있는지를 판단하고, 인과 추정(causal estimation)은 그 효과를 정량화한다. 어느 한 단계의 오류도 이후의 개입 의사결정에 전파될 수 있으므로 각 단계는 독립적으로 재현 가능해야 한다.

자동화된 인과 발견(automated causal discovery)은 발견된 그래프가 보장된 진실이 아니라 가설이기 때문에 추가적인 거버넌스(governance)를 필요로 한다. MLOps 파이프라인은 새로 학습된 구조를 도메인 제약, 이전 그래프 버전, 실험적 증거, 시간적 순서, 금지된 관계(forbidden relationship)와 비교할 수 있다. 새로운 데이터가 다른 그래프를 더 선호한다는 이유만으로 신뢰받던 인과 모델을 자동 교체하기보다 큰 구조 변화는 검토(review)를 촉발해야 한다.

인과 인공지능의 지속적 통합(Continuous Integration, CI)은 모델을 병합하거나 배포하기 전에 구조적 및 통계적 특성을 검사해야 한다. 자동 테스트는 필요한 경우 그래프의 비순환성(acyclicity), 변수 가용성, 시간적 순서, 개입 호환성, 조정 집합의 타당성, 추정기의 동작, 합성 인과 사례(synthetic causal case)에서의 예상 반응을 검증할 수 있다. 단위 테스트(unit test)는 소프트웨어가 변경되어도 유지되어야 하는 알려진 메커니즘을 명시적으로 포함할 수 있다.

지속적 배포(Continuous Delivery, CD)는 인과 출력이 실제 의사결정에 직접 영향을 미칠 때 일반적인 예측 서빙보다 더 강한 배포 게이트(deployment gate)를 필요로 한다. 후보 모델은 전체 권한을 부여받기 전에 오프라인 검증, 시뮬레이션, 섀도 배포(shadow deployment), 제한된 개입 테스트, 통제된 롤아웃(controlled rollout)을 통과할 수 있다. 배포 파이프라인은 단순히 인과 분석을 표시하는 시스템과 자동으로 개입을 선택하거나 실행하는 시스템을 구분해야 한다.

실험 관리(experiment management)는 인과 MLOps의 핵심 구성 요소이다. 무작위 시험(randomized trial), A/B 테스트(A/B testing), 통제된 로봇 실험, 시뮬레이션 연구, 자연 실험(natural experiment)을 모델 생명주기와 연결해야 한다. 실험 정의, 처치 할당, 결과, 제외 기준(exclusion), 중단 규칙(stopping rule), 분석 계획을 체계적으로 저장하여 새로운 인과 증거가 생성 당시의 맥락을 잃지 않고 모델을 갱신할 수 있도록 해야 한다.

관측 데이터(observational data)와 개입 데이터(interventional data)는 전체 파이프라인에서 구별된 상태를 유지해야 한다. 관측 데이터는 폭넓은 환경 커버리지(environmental coverage)를 제공하고, 개입 데이터는 특정 메커니즘에 대한 더 강한 증거를 제공한다. 이들을 결합하면 인과 학습을 개선할 수 있지만, 학습 시스템은 어떤 관계가 주로 상관관계에 의해 지원되고 어떤 관계가 직접적인 실험 증거를 가지고 있는지를 보존해야 한다.

검증 파이프라인(validation pipeline)은 별도로 분리된 데이터의 예측 정확도 이상을 테스트해야 한다. 인과 모델은 개입 효과 정확도(intervention-effect accuracy), 그래프 안정성(graph stability), 반사실적 일관성(counterfactual consistency), 환경 간 불변성(invariance), 불확실성 보정(uncertainty calibration), 교란에 대한 민감도, 후속 의사결정 품질을 평가해야 한다. 가능하면 예측된 개입 효과를 관측 데이터만으로 검증하기보다 무작위 또는 통제 실험의 결과와 비교해야 한다.

시뮬레이션(simulation)은 실제 배포 이전에 중요한 검증 계층(validation layer)을 제공한다. 합성 환경, 디지털 트윈(digital twin), 학습된 월드 모델(world model)은 현실에서 수행하기에 비용이 높거나 드물거나 위험한 개입을 생성할 수 있다. 실제 운영 시스템에 영향을 주기 전에 인과 모델을 메커니즘 변화, 센서 고장, 분포 변화(distribution shift), 극단적인 상태, 새로운 행동 조합에 노출시켜 검증할 수 있다.

배포 과정에서도 추론에 필요한 인과적 맥락(causal context)을 보존해야 한다. 서빙 엔드포인트(serving endpoint)가 임의의 특징 벡터(feature vector)를 받아 단순히 처치 효과를 반환해서는 안 된다. 필수 변수가 존재하는지, 값이 지원 범위 안에 있는지, 요청된 개입이 정의되어 있는지, 현재 환경이 모델이 검증된 조건과 유사한지를 확인해야 한다. 지원되지 않는 질의에는 정당화되지 않은 추정값을 반환하는 대신 불확실성을 표시하거나 요청을 거부해야 한다.

인과 모델 서빙(causal model serving)은 여러 형태의 출력을 제공할 수 있다. 서비스는 개입 효과, 반사실적 결과, 인과 경로(causal pathway), 권장 행동(recommended action), 불확실성 구간 또는 위반된 가정에 대한 경고를 제공할 수 있다. 후속 에이전트(agent)나 플래너(planner)가 조건부 예측을 개입 효과로 잘못 해석하여 잘못된 의사결정을 내리는 것을 방지하려면 인터페이스 계약(interface contract)이 각 출력의 정확한 의미를 명시해야 한다.

인과 인공지능의 모니터링은 데이터 드리프트(data drift)와 메커니즘 드리프트(mechanism drift)를 구분해야 한다. 데이터 드리프트는 관측 변수의 분포가 변화하는 것이고, 메커니즘 드리프트는 결과를 생성하는 인과관계 자체가 변화하는 것이다. 외형, 날씨, 사용자 모집단 또는 작업 부하의 변화는 인과 메커니즘을 무효화하지 않을 수 있지만, 하드웨어 열화, 정책 변화, 새로운 제어 로직, 변화된 물리 동역학은 메커니즘 자체를 직접 변경할 수 있다.

인과 잔차 모니터링(causal residual monitoring)은 이러한 변화를 탐지하는 데 도움을 줄 수 있다. 개입이 실행된 후 실제 관측 결과를 인과 모델이 예상했던 결과와 비교할 수 있다. 지속적인 불일치는 매개변수 드리프트(parameter drift), 구조적 변화(structural change), 숨겨진 교란(hidden confounding), 센서 문제 또는 지원되지 않는 운영 영역(unsupported operating regime)을 의미할 수 있다. 따라서 실제 개입은 배포된 인과 가정이 계속 신뢰 가능한지를 검증하는 지속적인 증거가 된다.

그래프 드리프트(graph drift) 역시 중요한 모니터링 대상이다. 새롭게 수집된 증거는 변수 사이의 관계가 변화했거나 이전에 안정적이었던 의존관계가 더 이상 유지되지 않는다는 것을 나타낼 수 있다. 그래프를 자동으로 재구성하기보다 후보 구조와 현재 배포된 버전을 비교하여 변경된 간선, 방향, 메커니즘, 불확실성을 식별할 수 있다. 의미 있는 구조적 드리프트는 조사와 재검증(revalidation)을 촉발해야 한다.

불확실성은 운영 정책에 직접 영향을 주어야 한다. 인과 서비스는 출력에 신뢰 구간, 사후 불확실성(posterior uncertainty), 구조적 모호성(structural ambiguity), 적용 가능성 점수(applicability score)를 함께 제공할 수 있다. 후속 시스템은 이를 이용하여 개입을 실행할지, 추가 관측을 요청할지, 시뮬레이션을 수행할지, 인간 운영자에게 검토를 요청할지, 또는 보수적인 대체 행동(conservative fallback action)을 선택할지를 결정할 수 있다. 따라서 불확실성은 단순한 보고 통계가 아니라 운영 제어 변수(operational control variable)가 된다.

인과 오류는 단순한 예측이 아니라 실제 행동에 영향을 줄 수 있기 때문에 롤백 메커니즘(rollback mechanism)이 필수적이다. 배포된 모든 인과 모델은 복구 가능한 이전 버전과 명확하게 정의된 대체 동작(fallback behavior)을 가져야 한다. 모니터링에서 예상하지 못한 개입 결과, 안전 위반, 심각한 드리프트 또는 인터페이스 비호환성이 탐지되면 이전에 검증된 그래프, 추정기, 정책 또는 규칙 기반 컨트롤러(rule-based controller)로 복원할 수 있어야 한다.

피지컬 인공지능(Physical AI)에서는 인과 MLOps가 소프트웨어 생명주기 관리와 하드웨어 구성을 연결해야 한다. 로봇 질량, 페이로드(payload), 타이어 상태, 액추에이터 특성, 센서 배치, 배터리 상태, 펌웨어(firmware), 컨트롤러 버전, 환경 조건은 실제 물리 메커니즘을 변화시킬 수 있다. 따라서 모델 메타데이터는 하나의 모델이 모든 상황에 적용된다고 가정하지 않고 각 인과 모델이 검증된 하드웨어 및 운영 영역(operating envelope)을 명확하게 식별해야 한다.

엣지 배포(edge deployment)는 로봇과 자율 장치가 네트워크 연결이 제한된 상황에서도 낮은 지연 시간과 높은 신뢰성으로 동작해야 하기 때문에 추가적인 제약을 만든다. 경량 인과 추론(lightweight causal inference), 안전 검사, 개입 평가는 로컬 장치에서 실행하고, 인과 발견, 대규모 시뮬레이션, 그래프 업데이트, 재학습은 온프레미스(on-premise) 또는 클라우드 인프라에서 수행할 수 있다. 동기화 메커니즘은 현재 동작 중인 제어를 방해하지 않으면서 검증된 모델 버전이 엣지에 전달되도록 해야 한다.

디지털 트윈은 모델 개발과 물리적 배포 사이의 스테이징 환경(staging environment)으로 활용될 수 있다. 후보 인과 모델은 먼저 로봇, 공장, 차량 또는 공정을 가상으로 표현한 시스템과 상호작용할 수 있다. 예측된 개입 결과와 시뮬레이션 결과의 차이는 모델의 약점을 나타내고, 디지털 트윈과 실제 물리 시스템 사이의 차이는 시뮬레이션 갭(simulation gap)을 나타낸다. 두 종류의 오류는 생명주기 전체에서 별도로 추적되어야 한다.

월드 모델과의 통합은 인과 MLOps가 예측 시뮬레이션을 또 하나의 버전 관리 대상 의존성(versioned dependency)으로 관리하도록 한다. 인과 플래너(causal planner)는 동시에 지각 모델, 상태 표현, 인과 그래프, 동역학 모델(dynamics model), 보상 함수(reward function), 안전 모델에 의존할 수 있다. 월드 모델이 변경되면 인과 그래프가 그대로 유지되어도 최종 행동 결정이 달라질 수 있으므로 배포 기록은 이러한 전체 의존성 집합을 함께 보존해야 한다.

인공지능 에이전트(AI agent)는 인과 출력이 자율적인 추론과 도구 사용(tool use)의 입력이 될 수 있기 때문에 또 다른 운영 계층을 추가한다. 에이전트 로그(agent log)는 어떤 인과 질의가 수행되었는지, 어떤 모델 버전이 응답했는지, 어떤 증거가 검색되었는지, 어떤 개입이 선택되었는지, 이후 어떤 결과가 발생했는지를 기록해야 한다. 이를 통해 관측에서 인과 추론, 행동, 결과까지 이어지는 감사 가능한 체인(auditable chain)을 구축할 수 있다.

거버넌스는 학습된 증거(learned evidence), 도메인 가정(domain assumption), 인간이 설정한 제약(human constraint)을 구별해야 한다. 일부 인과 간선은 실험적으로 검증되고, 다른 간선은 통계적으로 추론되며, 또 다른 간선은 물리 지식 또는 안전 요구사항 때문에 강제로 설정될 수 있다. 이러한 범주를 기록하면 검토자가 배포된 모델에 특정 관계가 포함된 이유를 이해할 수 있으며, 자동 재학습 과정에서 의도적으로 추가된 제약이 조용히 제거되는 것을 방지할 수 있다.

재현성(reproducibility)은 전체 인과 분석 환경을 패키징하는 것을 요구한다. 데이터 스냅샷(data snapshot), 그래프 정의, 추정기 설정, 난수 시드(random seed), 소프트웨어 의존성, 실험 기록, 평가 보고서, 배포 설정만으로 중요한 인과 결과를 재구성할 수 있어야 한다. 특히 개입에서 예상하지 못한 결과가 발생했을 때 엔지니어가 시스템이 왜 해당 의사결정을 내렸는지를 정확하게 추적해야 하므로 재현성의 가치가 더욱 커진다.

성숙한 인과 인공지능 MLOps 플랫폼(Causal AI MLOps Platform)은 데이터, 인과 발견, 추정, 실험, 검증, 배포, 모니터링, 수정(revision)을 연결하는 지속적인 순환 구조를 구축한다. 새로운 관측과 개입은 증거를 생성하고, 증거는 메커니즘을 갱신하며, 갱신된 메커니즘은 검증 게이트를 통과하고, 검증된 모델은 다시 운영 환경으로 배포된다. 이를 통해 인과 지식은 추적성과 안전성을 잃지 않으면서 지속적으로 발전할 수 있다.

인과 인공지능을 위한 MLOps의 궁극적인 목적은 단순히 인과 모델을 계속 실행 상태로 유지하는 것이 아니라 시스템과 환경이 변화하더라도 인과적 의사결정(causal decision)을 신뢰할 수 있도록 유지하는 것이다. 증거, 가정, 그래프, 개입, 불확실성, 실험, 하드웨어 맥락, 배포 이력을 운영의 핵심 산출물로 관리함으로써 조직은 인과 추론을 연구 단계의 기능에서 지속적으로 운영되는 인공지능 시스템의 신뢰 가능한 구성 요소로 전환할 수 있다.
