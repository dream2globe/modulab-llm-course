# Poetry 설치 가이드

## 기본 설치 방법

### Linux, macOS, Windows (WSL)

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

### Windows (Powershell)

```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

_Microsoft Store를 통해 Python을 설치한 경우 `py` 대신 `python` 사용_

## Poetry 설치 확인

```bash
poetry --version
```

## Poetry 업데이트

```bash
poetry self update
```

## 제거 방법

```bash
curl -sSL https://install.python-poetry.org | python3 - --uninstall
```

## Poetry 환경 변수 설정 방법 (자동 설정이 안된 경우)

- Windows는 시스템 환경변수 편집에서 추가 (%APPDATA%\Python\Script)

### 1. 설치 경로 확인

```bash
# 가상환경 경로 확인
where.exe poetry  # Windows
which poetry # Linux/macOS

# 기본 설치 경로
# macOS/Linux: $HOME/.local/bin/poetry
# Windows: %APPDATA%\Python\Scripts\poetry
```

### 2. PATH 설정

1. 설정 파일 열기

```bash
# zsh 사용시
nano ~/.zshrc

# bash 사용시
nano ~/.bash_profile
```

2. PATH 추가

```bash
export PATH="$HOME/.local/bin:$PATH"
```

3. 설정 적용

```bash
# zsh
source ~/.zshrc

# bash
source ~/.bash_profile
```

### 3. 설치 확인

```bash
poetry --version
```

만약 `command not found` 오류가 계속되면:

1. 정확한 설치 경로 재확인
2. PATH가 올바르게 설정되었는지 확인
3. 필요시 시스템 재시작


# Poetry 가상환경이 VS Code에서 인식되지 않는 경우:

1. VS Code에서 Python 확장 프로그램이 설치되어 있는지 확인
2. 터미널에서 다음 명령어로 poetry 환경 경로 확인
```bash
poetry env info --path
```
3. VS Code 명령 팔레트(Ctrl+Shift+P)에서 "Python: Select Interpreter" 선택 
4. "Enter interpreter path" 통해 위 경로 직접 입력


# Poetry 주요 명령어 정리

## 프로젝트 생성

### new

새 Python 프로젝트 생성

```bash
poetry new my-package
```

### init

`pyproject.toml` 대화식 생성

```bash
poetry init
```

## 의존성 관리

### install

의존성 설치

```bash
poetry install
```

### add

패키지 추가

```bash
poetry add requests
```

### remove

패키지 제거

```bash
poetry remove requests
```

### update

의존성 업데이트

```bash
poetry update           # 전체 업데이트
poetry update requests  # 특정 패키지만
```

## 빌드/배포

### build

패키지 빌드

```bash
poetry build
```

### publish

패키지 배포

```bash
poetry publish
poetry publish --build  # 빌드 후 배포
```

## 유틸리티

### run

가상환경에서 명령 실행

```bash
poetry run python script.py
```

### shell

가상환경 셸 진입

```bash
poetry shell
```

### config

설정 관리

```bash
poetry config --list
```

### check

`pyproject.toml` 검증

```bash
poetry check
```

## 환경 관리

### env info

가상환경 정보 조회

```bash
poetry env info
```

### env list

프로젝트의 가상환경 목록

```bash
poetry env list
```

### env remove

가상환경 삭제

```bash
poetry env remove <python>
```

### env use

사용할 Python 버전 지정

```bash
poetry env use python3.9
```

## 캐시 관리

### cache list

캐시 목록 조회

```bash
poetry cache list
```

### cache clear

캐시 삭제

```bash
poetry cache clear PyPI --all  # 전체 캐시
poetry cache clear pypi:requests:2.24.0  # 특정 패키지
```
