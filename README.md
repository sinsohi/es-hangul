# es-hangul Docker Project

## Goal

이 프로젝트는 한국어 텍스트 처리를 위한 **es-hangul 라이브러리**를 Docker 환경에서 실행하고, 오픈소스 컨트리뷰션을 통해 **표준 발음법 변환 기능의 버그를 수정**하는 것을 목표로 합니다.

구체적으로는 `standardizePronunciation` 함수의 **제12항 [붙임 2] 조항**이 누락된 문제를 해결하여, 받침 'ㅅ, ㅈ, ㅊ, ㅌ'이 뒤 음절 첫소리 'ㅎ'과 결합될 때 올바른 발음 변환이 이루어지도록 개선했습니다.

## Requirements

Docker 환경에서 다음 라이브러리들이 설치됩니다:

- **Node.js**: >= 20.0.0
- **yarn**: = 4.1.1
- **git**: latest
- **vim**: latest

## How to install & Run

### Docker image 다운로드 및 설치하는 방법

```bash
# 1. tar 파일을 Docker 이미지로 로드
docker load -i final_2023040036_v1.tar

# 2. 이미지가 정상적으로 로드되었는지 확인
docker images
```
### Docker container 생성하고 실행하는 방법

```bash
# 1. 컨테이너 생성 및 백그라운드 실행
docker run -dit final_2023040036:v1

# 2. 실행 중인 컨테이너 확인
docker ps

# 3. 컨테이너에 접속 (CONTAINER_ID는 위에서 확인한 ID 사용)
docker exec -it <CONTAINER_ID> /bin/bash

# 4. 프로젝트 디렉토리로 이동
/# cd ~/es-hangul

# 5. 예제 코드 실행
~/es-hangul# node index.js
```

### 디렉토리 구조

```
/root/
└── es-hangul/                  
    ├── package.json            
    ├── src/                    
    ├── dist/                   # 컴파일된 JavaScript 파일
    │   └── index.js           # 빌드된 라이브러리
    ├── index.js               # 실행 예제 파일
    └── README.md              
```
### 실행을 마치고 종료하는 방법

```bash
# 1. 컨테이너에서 나가기
exit

# 2. 컨테이너 중지
docker stop <CONTAINER_ID>

# 3. 컨테이너 삭제 
docker rm <CONTAINER_ID>

# 4. 이미지 삭제
docker rmi final_2023040036:v1
```

