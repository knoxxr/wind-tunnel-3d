# AERO LAB 3D — 3D 풍동 실험 시뮬레이션

브라우저에서 별도 백엔드나 빌드 도구 없이 바로 실행되는 **WebGL2 기반 실시간 3D 풍동(Wind Tunnel) 시뮬레이션**입니다.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fknoxxr%2Fwind-tunnel-3d)

## 주요 기능

- **기본 자동차 & 비교 프리셋 모델**
  - **GT 스포츠카 (기본)**: 패스트백 차체, 프론트 스플리터, 리어 디퓨저, 인버티드 에어포일 리어 윙, 4륜 스포크 휠(롤링 로드 연동 회전)
  - **SUV**, **F1 레이서**, **NACA 2412 에어포일**, **표준 구체(Sphere)** 비교 프리셋
- **사용자 3D 모델 업로드 및 실시간 교체**
  - `.glb`, `.gltf`, `.obj`, `.stl` (Binary / ASCII 모두 지원) 파일 선택 또는 드래그 앤 드롭
  - 자동 크기 정규화, 중심 정렬, 지면 안착, 전면 축(`-X/+X/-Z/+Z`) 및 상단 축(`Y-Up / Z-Up`) 원클릭 보정
  - 테스트용 `.obj` 내보내기 기능 제공
- **실시간 3D 복셀 CFD 유동 해석**
  - 임의의 업로드 삼각형 메시를 3D 복셀 그리드로 래스터화하고 3D Laplace 포텐셜 유동(Red-Black SOR) + 점성 후류(Wake)·박리·후류 와류 모델 결합
  - 실시간 항력 계수($C_d$), 항력($F_D$), 다운포스/양력($C_L, F_L$), 횡력($F_Y$), 전면 투영 면적($A$), 동압($q$), 레이놀즈 수($Re$), 중심선 $C_p$ 압력 분포 그래프 계산
- **다양한 3D 풍동 시각화**
  - 3D 볼류메트릭 스모크 유선(수직 콤브 / 수평 콤브 / 3D 매트릭스)
  - 3D 기류 파티클 스트릭(난류 후류 반영)
  - 모델 표면 압력 분포 히트맵($C_p$ 등압선) / 스튜디오 메탈릭 / 와이어프레임 모드
  - 이동 가능한 2D 단면 유동 슬라이스(종단 $Z$, 수평 $Y$, 후류 $X$)
  - 롤링 로드(이동 바닥), 요각 회전 턴테이블, 다크/라이트 스튜디오 테마 전환

## Vercel 배포 방법

1. 상단의 **Deploy with Vercel** 버튼을 클릭하거나 [Vercel Import 페이지](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fknoxxr%2Fwind-tunnel-3d)에서 저장소를 연결해 원클릭 배포합니다.
2. 또는 로컬에서 CLI로 배포할 수 있습니다:
   ```bash
   npx vercel --prod
   ```
