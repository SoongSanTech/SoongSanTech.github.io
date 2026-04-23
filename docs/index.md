---
title: SoongSanTech (SIT) - 자율주행 연구 지식 위키
hide:
  - navigation
  - toc
---

<div class="hero-section" markdown>

<span class="hero-eyebrow">AUTONOMOUS DRIVING RESEARCH LAB</span>

# 디지털 트윈에서 현실까지,<br>Sim-to-Real 자율주행을 연구합니다.

<p class="hero-lead">
숭산텍(SIT)은 소규모 R&D 팀으로서, CARLA 시뮬레이터 기반의 행동복제(BC)와 강화학습(PPO) 파이프라인을 구축하고 엣지 디바이스(Jetson)에서의 실시간 제어 실증을 목표로 합니다. 연구의 모든 과정을 이 공간에 투명하게 기록합니다.
</p>

<a href="knowledge/index.md" class="hero-cta">지식저장소 둘러보기 →</a>
<a href="rnd/index.md" class="hero-cta secondary">R&D 로그 보기</a>

</div>

<div class="grid cards" markdown>

-   :material-book-open-page-variant:{ .lg .middle } **지식 위키 (Docs)**

    ---

    자율주행, 강화학습, CARLA 시뮬레이터, ROS2 등 프로젝트 관련 핵심 개념과 시스템 아키텍처, 기술 스택 가이드를 체계적으로 정리합니다.

    [:octicons-arrow-right-24: 지식저장소 둘러보기](knowledge/index.md)

-   :material-flask:{ .lg .middle } **R&D 로깅 (Blog)**

    ---

    실험 설정, 진행 경과, 결과 분석, 트러블슈팅 등 자율주행 모델 연구 개발의 전 과정을 시계열로 투명하게 기록하고 추적합니다.

    [:octicons-arrow-right-24: 최근 실험 로그 보기](rnd/index.md)

-   :material-github:{ .lg .middle } **오픈소스 생태계**

    ---

    모든 연구 결과물과 소스 코드는 GitHub를 통해 공개되며, 자율주행 연구 커뮤니티의 발전에 기여하고자 합니다.

    [:octicons-arrow-right-24: GitHub 레포지토리](https://github.com/SoongSanTech/Autonomous-Driving-Planning)

-   :material-account-group:{ .lg .middle } **협업 가이드**

    ---

    팀원들이 쉽게 문서를 작성하고 기여할 수 있도록 표준화된 마크다운 템플릿과 PR 워크플로우를 제공합니다.

    [:octicons-arrow-right-24: 기여 방법 알아보기](contact/index.md)

</div>

<div class="section-header">
  <h2 class="section-header__title">Recent R&D Logs</h2>
  <a href="rnd/index.md" class="section-header__more">View All →</a>
</div>

<div class="blog-featured">
  <div class="blog-featured__image">
    <img src="assets/img/rnd/post_carla.png" alt="Phase 1 Pipeline">
  </div>
  <div class="blog-featured__body">
    <span class="blog-featured__category">Phase 1</span>
    <h3 class="blog-featured__title">
      <a href="rnd/posts/2026-04-22-phase1-pipeline/">데이터 파이프라인 구축: Phase 1 진행 현황</a>
    </h3>
    <p class="blog-featured__excerpt">
      CARLA 시뮬레이터에서 수집한 주행 데이터를 정제·검증·저장하는 파이프라인 1차 MVP를 완성했습니다. 89개의 단위 테스트와 Property-Based Testing을 통해 품질을 검증하며, 2만 프레임 규모의 데이터셋을 안정적으로 처리할 수 있습니다.
    </p>
    <div class="blog-featured__meta">2026.04.22 · 8분 읽기</div>
    <div class="blog-featured__tags">
      <span class="hashtag">DataPipeline</span>
      <span class="hashtag">CARLA</span>
      <span class="hashtag">Phase1</span>
    </div>
  </div>
</div>

<div class="blog-grid">

  <article class="blog-card">
    <div class="blog-card__image">
      <img src="assets/img/rnd/post_bc_rl.png" alt="BC to RL Pipeline">
    </div>
    <div class="blog-card__body">
      <span class="blog-card__category">Research</span>
      <h4 class="blog-card__title">
        <a href="knowledge/category/이론-(theory)/">BC → PPO 2단계 학습 전략</a>
      </h4>
      <p class="blog-card__excerpt">
        행동복제로 초기 정책을 확보한 뒤 PPO로 미세조정하는 2단계 접근을 코드 수준에서 구현했습니다.
      </p>
      <div class="blog-card__footer">
        <span class="hashtag">ReinforcementLearning</span>
        <span>2026.04</span>
      </div>
    </div>
  </article>

  <article class="blog-card">
    <div class="blog-card__image">
      <img src="assets/img/rnd/post_tensorrt.png" alt="TensorRT Quantization">
    </div>
    <div class="blog-card__body">
      <span class="blog-card__category">Engineering</span>
      <h4 class="blog-card__title">
        <a href="knowledge/category/기술-스택-(tech-stack)/">TensorRT 양자화로 30Hz 달성하기</a>
      </h4>
      <p class="blog-card__excerpt">
        FP16/INT8 양자화를 적용해 Jetson Orin에서 ResNet18 기반 모델을 30Hz로 안정 추론합니다.
      </p>
      <div class="blog-card__footer">
        <span class="hashtag">TensorRT</span>
        <span>2026.04</span>
      </div>
    </div>
  </article>

  <article class="blog-card">
    <div class="blog-card__image">
      <img src="assets/img/rnd/post_ros2.png" alt="ROS2 Humble">
    </div>
    <div class="blog-card__body">
      <span class="blog-card__category">System</span>
      <h4 class="blog-card__title">
        <a href="knowledge/category/시스템-아키텍처-(architecture)/">ROS2 Humble 통합 아키텍처</a>
      </h4>
      <p class="blog-card__excerpt">
        센서·인지·계획·제어 노드를 pub-sub 메시지로 연결한 분산 시스템을 구성했습니다.
      </p>
      <div class="blog-card__footer">
        <span class="hashtag">ROS2</span>
        <span>2026.04</span>
      </div>
    </div>
  </article>

</div>

<div class="section-header">
  <h2 class="section-header__title">Research Tags</h2>
  <a href="knowledge/아카이브/" class="section-header__more">Knowledge Archive →</a>
</div>

<div class="tag-cloud">
  <a href="#">CARLA</a>
  <a href="#">BehavioralCloning</a>
  <a href="#">PPO</a>
  <a href="#">ReinforcementLearning</a>
  <a href="#">SimToReal</a>
  <a href="#">ResNet18</a>
  <a href="#">TensorRT</a>
  <a href="#">Quantization</a>
  <a href="#">Jetson</a>
  <a href="#">ROS2</a>
  <a href="#">EdgeComputing</a>
  <a href="#">PyTorch</a>
  <a href="#">DataPipeline</a>
  <a href="#">DigitalTwin</a>
  <a href="#">AutonomousDriving</a>
  <a href="#">ImitationLearning</a>
  <a href="#">PropertyBasedTesting</a>
  <a href="#">MLOps</a>
  <a href="#">Sim2Real</a>
  <a href="#">DomainRandomization</a>
</div>

---

## 핵심 연구 방향성

숭산텍의 자율주행 프로젝트는 **"엣지 디바이스 제약 하의 Sim-to-Real 경량 자율주행 시스템 구현 및 체계적 실증 분석"** 이라는 단일 명제를 중심으로 구성되어 있습니다. 새로운 모델을 발명하기보다는, 완전한 Sim-to-Real 파이프라인을 구축하고 그 위에서 체계적 실증 실험을 수행하는 것이 이 프로젝트의 차별점입니다.

| 원칙 | 내용 |
|------|------|
| **Sim-First** | 모든 학습과 검증은 CARLA 시뮬레이터에서 선행 |
| **BC → RL** | 행동복제로 초기 정책 확보 후 PPO 강화학습으로 미세조정 |
| **시스템 우선** | 검증된 모델(ResNet18) 채택으로 파이프라인 실증에 집중 |
| **엣지 최적화** | Jetson 환경에서 30Hz 제어를 위한 TensorRT 양자화 (FP16/INT8) |
| **실증 연구** | 파이프라인 기반 체계적 실험으로 학술적 기여 도출 |

자세한 내용은 [프로젝트 개요](about/project-overview.md)를 참고하세요.
