# <p align="center">프로젝트 환경 구성 안내 (Setup Guide)</p>

## 1. 프로젝트 개요 (Project Overview)

본 문서는 '사이버 정보 체계 운용 초급반 시간표 자동 생성 프로젝트'의 개발 및 실행 환경을 구성하는 방법을 안내합니다.

---

## 2. 기술 스택 (Technology Stack)

- **Backend:** Node.js, Express
- **Frontend:** React, TailwindCSS, react-big-calendar
- **Database:** SQLite
- **Version Control:** Git

---

## 3. 환경 구성 (Environment Setup)

### 3.1. 공통 (Common)

#### 1. Git 설치
- Git을 설치하여 소스 코드를 관리합니다.
- 다운로드: [https://git-scm.com/downloads](https://git-scm.com/downloads)

#### 2. Node.js 및 npm 설치
- 백엔드와 프론트엔드 모두 Node.js를 사용합니다.
- **Node.js 16 이상** 및 **npm 8 이상** 설치를 권장합니다.
- 다운로드: [https://nodejs.org/](https://nodejs.org/) (LTS 버전 권장)

### 3.2. 백엔드 (Backend) - Node.js / Express

- 백엔드 소스코드를 관리할 디렉터리(예: `backend/`)를 생성하고 해당 디렉터리에서 다음을 진행합니다.

#### 1. `package.json` 생성
- 다음 명령어를 실행하여 `package.json` 파일을 생성합니다.
  ```bash
  npm init -y
  ```

#### 2. 필요 패키지 설치
- 다음 명령어를 실행하여 Express 및 관련 패키지를 설치합니다.
  ```bash
  npm install express sqlite3 multer
  # `sqlite3`는 SQLite 데이터베이스와 상호작용하기 위함입니다.
  # `multer`는 엑셀 파일 업로드를 처리하기 위함입니다.
  ```
- 개발 편의를 위해 `nodemon`을 설치할 수 있습니다.
  ```bash
  npm install -D nodemon
  ```

### 3.3. 프론트엔드 (Frontend) - React (with Vite)

- 프론트엔드 소스코드를 관리할 디렉터리(예: `frontend/`)를 생성하고, 해당 디렉터리로 이동하여 다음을 진행합니다.

#### 1. React 앱 생성 (Vite)
- Vite를 사용하여 현재 디렉터리에 React 프로젝트를 생성합니다.
  ```bash
  npm create vite@latest . -- --template react
  ```

#### 2. 필요 패키지 설치
- 다음 명령어를 실행하여 프로젝트 기본 의존성을 설치합니다.
  ```bash
  npm install
  ```
- 이어서 애플리케이션에 필요한 라이브러리를 설치합니다.
  ```bash
  npm install tailwindcss postcss autoprefixer react-router-dom react-big-calendar axios
  ```

#### 3. TailwindCSS 설정
- 다음 명령어를 실행하여 TailwindCSS 설정 파일을 생성합니다.
  ```bash
  npx tailwindcss init -p
  ```
- 생성된 `tailwind.config.js` 파일을 열고, `content` 부분을 프로젝트 파일 경로에 맞게 수정해야 합니다.
- `src/index.css` 파일 상단에 다음 내용을 추가하여 TailwindCSS를 전역으로 적용합니다.
  ```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
  ```

---

## 4. 데이터베이스 설정 (Database Setup)

- 본 프로젝트는 **SQLite**를 사용하므로 별도의 데이터베이스 서버 설치가 필요 없습니다.
- 백엔드 서버를 처음 실행하면 프로젝트의 백엔드 디렉터리에 `database.sqlite` 와 같은 데이터베이스 파일이 자동으로 생성됩니다.

---

## 5. 실행 방법 (How to Run)

### 5.1. 백엔드 서버 실행
- 백엔드 디렉터리(예: `backend/`)로 이동합니다.
- 다음 명령어를 실행하여 서버를 시작합니다. (메인 서버 파일이 `server.js`라고 가정)
  ```bash
  node server.js
  ```
- 또는 `nodemon`을 사용하는 경우:
  ```bash
  nodemon server.js
  ```
- 서버는 보통 `http://localhost:8000` 또는 설정된 포트에서 실행됩니다.

### 5.2. 프론트엔드 개발 서버 실행
- 프론트엔드 디렉터리(예: `frontend/`)로 이동합니다.
- 다음 명령어를 실행하여 개발 서버를 시작합니다.
  ```bash
  npm start
  ```
- 애플리케이션은 `http://localhost:3000` 에서 열립니다.

---

## 6. 초기 데이터 설정 (Initial Data Setup)

- 시스템을 사용하기 위해 초기 교과목 데이터가 필요합니다.
- `prd.md` 문서의 4.1. 항목에 명시된 양식에 따라 '교과목.xlsx' 파일을 작성합니다.
- 웹 UI의 '교과목 관리' 페이지에서 해당 엑셀 파일을 업로드하여 초기 데이터를 설정합니다.
