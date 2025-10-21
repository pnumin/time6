Windows에서 SQLite를 설치하는 방법 

## SQLite 설치 방법

### 1. SQLite 다운로드

1. **공식 웹사이트 방문**
   - https://www.sqlite.org/download.html 접속

2. **Windows용 파일 다운로드**
   - "Precompiled Binaries for Windows" 섹션에서 다음 파일들을 다운로드:
     - `sqlite-tools-win32-x86-*.zip` (SQLite 명령줄 도구)
     - `sqlite-dll-win64-x64-*.zip` (64비트 DLL, 필요한 경우)

### 2. 압축 해제 및 설치

1. **다운로드한 ZIP 파일 압축 해제**
   - 원하는 위치에 폴더 생성 (예: `C:\sqlite`)
   - ZIP 파일을 해당 폴더에 압축 해제
   - 주요 파일: `sqlite3.exe`, `sqldiff.exe`, `sqlite3_analyzer.exe`

### 3. 환경 변수 설정 (선택사항이지만 권장)

1. **시스템 환경 변수 열기**
   - Windows 검색에서 "환경 변수" 검색
   - "시스템 환경 변수 편집" 선택
   - "환경 변수" 버튼 클릭

2. **Path 변수에 SQLite 경로 추가**
   - "시스템 변수" 섹션에서 "Path" 선택 후 "편집" 클릭
   - "새로 만들기" 클릭
   - SQLite 폴더 경로 입력 (예: `C:\sqlite`)
   - "확인"으로 모든 창 닫기

### 4. 설치 확인

1. **명령 프롬프트 열기**
   - Windows 검색에서 "cmd" 또는 "명령 프롬프트" 검색

2. **SQLite 버전 확인**
   ```cmd
   sqlite3 --version
   ```

3. **SQLite 실행**
   ```cmd
   sqlite3
   ```
   - 성공적으로 실행되면 `sqlite>` 프롬프트가 나타남
   - 종료하려면 `.quit` 또는 `.exit` 입력

### 5. 기본 사용법

```cmd
# 새 데이터베이스 생성 또는 기존 데이터베이스 열기
sqlite3 mydatabase.db

# 테이블 생성 예시
sqlite> CREATE TABLE users (id INTEGER PRIMARY KEY, name TEXT, email TEXT);

# 데이터 삽입
sqlite> INSERT INTO users (name, email) VALUES ('홍길동', 'hong@example.com');

# 데이터 조회
sqlite> SELECT * FROM users;

# 종료
sqlite> .quit
```

## 추가 팁

- **GUI 도구 사용**: 명령줄이 불편하다면 DB Browser for SQLite (https://sqlitebrowser.org/) 같은 GUI 도구를 사용할 수 있습니다.
- **프로그래밍 언어에서 사용**: Python, Java, C# 등 대부분의 프로그래밍 언어에서 SQLite 라이브러리를 제공하므로 별도 설치 없이 바로 사용 가능합니다.
 