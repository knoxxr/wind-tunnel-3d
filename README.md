# AERO LAB 3D — 3D 풍동 실험 시뮬레이션

별도 백엔드 서버 없이 브라우저의 WebGL2와 클라이언트 측 3D CFD 솔버로 동작하는 **고동시성 정적 3D 풍동 시뮬레이션**입니다.

## 주요 기능

- **기본 자동차 & 비교 프리셋 모델**: GT 스포츠카(기본), SUV, F1 레이서, NACA 2412 에어포일, 표준 구체
- **사용자 3D 모델 업로드**: `.glb`, `.gltf`, `.obj`, `.stl` (Binary/ASCII, 최대 50MB 안전 가드), 자동 정규화 및 축 방향 보정
- **실시간 3D 복셀 CFD 해석**: 항력 계수($C_d$), 항력($F_D$), 다운포스/양력($C_L, F_L$), 횡력($F_Y$), 전면 투영 면적($A$), 동압($q$), 레이놀즈 수($Re$), 중심선 $C_p$ 분포 그래프
- **3D 풍동 시각화**: 3D 스모크 유선, 기류 파티클, 모델 표면 압력($C_p$) 히트맵, 2D 단면 슬라이스, 롤링 로드 및 요각 턴테이블
- **다중 동시 접속 최적화**:
  - **100% 클라이언트 독립 실행**: 모든 3D 렌더링·모델 파싱·유동 해석이 각 접속자 브라우저에서 독립 수행되어 동시 접속자가 급증해도 서버 병목 없음
  - **외부 CDN 의존성 제거**: 사전 컴파일된 정적 [styles.css](./styles.css)만 사용하여 외부 CDN 장애·학교/사내망 차단 영향 없음
  - **Vercel Global Edge CDN 캐싱**: `vercel.json`에 정적 에셋 `immutable` 및 `stale-while-revalidate` 헤더 적용
  - **안정성 및 다중 기기 대응**: GPU 버퍼 명시적 해제(VRAM 누수 방지), WebGL 컨텍스트 손실 자동 복구, 백그라운드 탭 절전(`visibilitychange`), 모바일 패널 자동 접힘
  - **실험 조건 URL 공유(`공유` 버튼)**: 현재 풍속·요각·피치·프리셋·시각화 설정을 URL 링크로 복사해 여러 명이 동일한 실험 조건으로 동시 접속 가능

## Vercel 배포 방법

1. [Vercel Import 페이지](https://vercel.com/new/import?s=https%3A%2F%2Fgithub.com%2Fknoxxr%2Fwind-tunnel-3d)에서 `knoxxr/wind-tunnel-3d` 저장소를 선택하고 **Deploy**를 클릭합니다.
2. 이후 `main` 브랜치에 푸시할 때마다 Vercel이 자동으로 재배포합니다.
