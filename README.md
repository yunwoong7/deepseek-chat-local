<h2 align="center">
Deepseek-chat-local
</h2>

<div align="center">
  <img src="https://img.shields.io/badge/Ollama-Local%20AI-black"/>
  <img src="https://img.shields.io/badge/Docker-Container-2496ED"/>
  <img src="https://img.shields.io/badge/OpenWebUI-Interface-4A90E2"/>
</div>

로컬 환경에서 실행되는 AI 채팅 애플리케이션으로, Deepseek R1 모델과 Ollama를 활용하여 구축되었습니다. 실시간 대화, 모델 선택 드롭다운 메뉴, 직관적인 Open Web UI 인터페이스를 제공합니다.

## 준비 단계: 필수 프로그램 설치

### 1. Ollama 설치하기

1. [Ollama 공식 웹사이트](https://ollama.com) 접속
2. 운영체제에 맞는 버전 다운로드:
   - **Windows**: [Ollama Windows Preview](https://ollama.com/download/windows)
   - **macOS**: `brew install ollama`
   - **Linux**: `curl -fsSL https://ollama.com/install.sh | sh`
3. 설치 완료 후 터미널에서 실행 확인:
   ```bash
   ollama --version
   ```

### 2. Docker 설치하기

1. [Docker 공식 웹사이트](https://www.docker.com) 접속
2. Docker Desktop 다운로드 및 설치
3. 설치 완료 후 실행 상태 확인:
   ```bash
   docker --version
   ```

> 💡 **참고**: Docker 계정 생성은 선택사항입니다.

## 메인 설치 과정

### 1. Ollama 서비스 시작

새 터미널 창을 열고 Ollama 서비스 시작:
```bash
ollama serve
```

> ⚠️ **중요**: 이 터미널 창은 열어둔 채로 유지해야 합니다. 서비스가 실행 중이어야 다음 단계를 진행할 수 있습니다.

### 2. OpenWebUI 설치 및 접속

1. 새로운 터미널 창을 열고 Docker가 실행 중인지 확인
2. OpenWebUI 설치 및 실행:
   ```bash
   docker run -d -p 3000:8080 \
   -v ollama:/root/.ollama \
   -v open-webui:/app/backend/data \
   --name open-webui --restart always \
   ghcr.io/open-webui/open-webui:ollama
   ```

> 💡 **설치 과정 설명**: 
> - Docker 이미지 다운로드 (처음 실행시에만)
> - 컨테이너 생성 및 설정
> - 데이터 저장을 위한 볼륨 생성
> - 웹 서버 시작
> 
> ⏱️ 첫 실행시 이미지 다운로드로 인해 1-2분 정도 소요될 수 있습니다.

3. 설치 완료 확인:
   ```bash
   docker ps
   ```
   OpenWebUI 컨테이너가 목록에 표시되면 정상적으로 실행된 것입니다.

4. 브라우저에서 `http://localhost:3000` 접속
5. 첫 계정 생성 (자동으로 관리자 권한 부여)

> 💡 **참고**: 
> - `ollama serve`가 실행 중이지 않으면 OpenWebUI가 Ollama에 연결할 수 없습니다
> - 연결 오류가 발생하면 `ollama serve`가 실행 중인지 확인해주세요

### 3. DeepSeek R1 모델 설치

1. OpenWebUI에서 모델 설치:
   - 상단 메뉴에서 '설정' → '관리자 설정' 클릭
   - 'Manage Models' 선택
   - 'Add New Model' 클릭
   - Model Name에 `deepseek-r1:latest` 입력
   - 'Download' 버튼 클릭하여 설치 시작
   
2. 설치 진행 상태는 화면에서 확인 가능합니다.

> 💡 **참고**: 
> - 첫 설치는 모델 크기에 따라 시간이 걸릴 수 있습니다
> - 설치가 완료되면 자동으로 모델 선택 드롭다운에 표시됩니다

## 🎯 시작하기

1. OpenWebUI에 접속 (`http://localhost:3000`)
2. 상단 모델 선택 드롭다운에서 'deepseek-r1' 선택
3. 채팅 시작!

<div align="center">
<img src="https://blog.kakaocdn.net/dn/MMOlr/btsL533Rdtj/EqCIIJxRjR9Pzm85uLhU1K/img.gif" width="70%">
</div>
