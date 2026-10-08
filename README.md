---
md-id: 537e9ab6-a1d8-41ed-9470-331b07e9d287
---
# no-doc-no-nrs-plan
젓가락 교정 어플리케이션

# 프로젝트 개요
- 사용자가 카메라 앞에서 젓가락을 움직이면 AI가 손가락과 젓가락의 움직임을 분석
- 아래 젓가락의 안정성, 위 젓가락의 독립 움직임, 손가락의 지지 위치 등을 측정
- 단순한 정답·오답이 아니라 어떤 동작을 먼저 고쳐야 하는지 알려주는 맞춤형 교정 피드백을 제공

## 기술 구현 목표
- 5~10초의 젓가락 동작을 촬영해 분석하는 앱을 구현
    - MediaPipe Hand Landmarker 모델을 활용하여 영상에서 손가락 랜드마크를 실시간 추적
    - 선행연구에서 활용된 손가락–젓가락 간 거리와 프레임별 위치 변화를 바탕으로 손가락 지지와 젓가락 움직임을 분석
        1) 손의 21개 랜드마크와 젓가락 위치를 실시간으로 추적
        2) 아래 젓가락 안정성, 위 젓가락 독립성, 손가락 지지, 젓가락 교차 여부를 분석
        3) 가장 큰 문제를 화면에 표시하고 교정 방법을 제안
- OpenAI API를 활용해 분석 결과 중 우선적으로 교정해야 할 문제를 선택
- 사용자가 바로 이해하고 따라 할 수 있는 자연어 피드백으로 변환
    - 예를 들어 “아래 젓가락 안정성 42%. 위 젓가락과 함께 움직이고 있습니다. 약지 위에 아래 젓가락을 고정하고 위 젓가락만 움직여 보세요.”
    - 단순한 정답/오답 판정을 넘어 원인파악과 개선안을 제시

## 기술 스택
- MediaPipe Hand Landmarker
- OpenCV/JavaScript 또는 Python
- Web Camera API
- OpenAI API
- 웹 기반 프론트엔드

## 참고문헌
- 강경희·안성지·김형신, 「아동 소근육 발달을 위한 인터랙티브 젓가락 게임 제안」, _HCI Korea 2023_, 2023.
- Choji et al., “Factors influencing chopstick use and an objective identification of traditional holding techniques in children,” _PLOS ONE_, 2025.
- Choji et al., “Impact of a mobile application and assistive chopsticks on traditional chopstick manipulation,” _Disability and Rehabilitation: Assistive Technology_, 2026.

# 프로젝트 구성
## Codex
## OpenRig
- 멀티 에이전트 오케스트라이제이션 프로그램
- 전용 Conda 환경: `openrig`; 설치 경로는 각 컴퓨터의 환경에 따라 지정.
- 설치 버전: OpenRig 0.6.6, Node.js 24.21.0, npm 11.19.0, tmux 3.4.
- Codex 테스트 프로필: `openrig-addition`; 해당 소유자의 Codex 설정 경로에 구성.
- 실행 권한: 테스트 작업 폴더와 상태 폴더에 쓰기 허용, 명령 네트워크 차단, 권한 확대 차단.
- 2026-10-08 검증: 에이전트 실행, 덧셈 메시지 전달, `2 + 3`에 대한 `결과: 5` 응답 확인.
- 검증 범위: Codex 단일 에이전트 실행과 응답 확인; 다중 에이전트 협업은 미검증.
- 기본 kernel은 실행하지 않았으며, 테스트 작업 공간은 임시 구성.
- 설치·검증 결과와 대상 환경의 실행 방법: [OpenRig 인계 문서](docs/ai-generated-openrig-install-verification-handoff.md).
- 개인화된 경로와 로컬 운영 기록은 Git 제외 대상인 `etc/`에 보관; 외부 공유 시 제외.
## Git
- 두 팀원의 협업
