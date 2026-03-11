# 🐳 [오픈소스SW분석] 도커 이미지와 컨테이너

[cite_start]**단국대학교 AI융합대학 컴퓨터공학과 / 네트워크 시스템 및 보안 연구실 (BoanLab)** [cite: 4, 5, 6]
[cite_start]**강의자:** 남재현 교수님 (namjh@dankook.ac.kr) [cite: 3, 746]

> [cite_start]이 저장소는 오픈소스SW분석 (클라우드) 과목의 두 번째 파트인 **'도커 이미지와 컨테이너'** 강의 실습을 위한 가이드와 명령어 모음을 제공합니다. [cite: 1, 2]

---

## 🎯 학습 목표 (Core Concepts)

본 강의를 통해 도커의 핵심 구조를 이해하고, 실무에 필요한 컨테이너 제어 및 이미지 관리 능력을 습득합니다.

* [cite_start]**읽기 전용 이미지와 읽기/쓰기 컨테이너의 차이** 이해 [cite: 98, 99]
* [cite_start]**유니온 파일시스템(Union Filesystem)과 OverlayFS**의 계층(Layer) 구조 파악 [cite: 190, 191, 210]
* [cite_start]컨테이너의 전체 **라이프사이클 (생성 ➔ 실행 ➔ 일시정지 ➔ 중지 ➔ 삭제)** 제어 [cite: 142, 172, 174, 176]
* [cite_start]환경변수 주입, 포트 매핑, 볼륨 마운트를 활용한 **Nginx 웹 서버 컨테이너 배포** [cite: 195, 197, 263]
* [cite_start]이미지 백업/복원(`save`/`load`) 및 컨테이너 마이그레이션(`export`/`import`, `commit`) [cite: 616, 672]
* [cite_start]실운영 환경을 위한 **트러블슈팅(로그 분석, 권한 오류 해결) 및 성능 최적화** [cite: 698, 717, 724]

---

## 💻 실습 환경 준비 (Prerequisites)

[cite_start]강의 자료의 기본 실습 명령어는 아래의 환경을 기준으로 작성되었습니다. [cite: 10]

* [cite_start]**OS:** Ubuntu 24.04 LTS (Noble Numbat) [cite: 10]
* [cite_start]**Architecture:** x86_64(amd64), arm64 지원 [cite: 17, 18]

💡 **macOS 사용자 안내:** 터미널을 통한 리눅스 패키지 설치(`apt-get`) 과정 대신, [Docker Desktop for Mac]을 설치하여 엔진을 구성한 후 **컨테이너 실행 및 제어** 단계부터 동일하게 실습을 진행할 수 있습니다.

---

## 📂 리포지토리 구성 (Repository Structure)

실습의 편의를 위해 명령어들을 목적별로 분류해 두었습니다. 각 섹션의 상세 명령어는 본 저장소의 치트시트를 참고하세요.

1.  [cite_start]**[환경 구축]** 도커 엔진 설치 및 권한 설정 (`apt-get`, `usermod`) [cite: 19, 82]
2.  [cite_start]**[기본 제어]** 컨테이너 실행 및 라이프사이클 관리 (`run`, `stop`, `kill`, `rm`) [cite: 234, 391, 410]
3.  [cite_start]**[모니터링]** 컨테이너 내부 접속 및 상태/로그 확인 (`ps`, `exec`, `logs`, `inspect`) [cite: 293, 434, 459]
4.  [cite_start]**[이미지 관리]** 레지스트리 인증 및 이미지 빌드/배포 (`pull`, `push`, `tag`, `history`) [cite: 525, 577, 598]
5.  [cite_start]**[데이터 백업]** 폐쇄망 이관 및 마이그레이션 (`save`/`load`, `export`/`import`) [cite: 616, 676, 678]

---

## 🛠️ 주요 실습 가이드 바로가기

*웹 서버 배포 실습 등 상세한 명령어 실행 코드는 별도의 마크다운 파일(예: `commands.md`)을 참고하거나 아래 섹션에 추가해 주세요.*
