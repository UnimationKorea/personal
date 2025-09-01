# 🚀 Cloudflare Pages 배포 가이드

## 현재 상황
- ✅ **코드 준비 완료**: 모든 파일이 GitHub에 업로드됨
- ✅ **GitHub 저장소**: https://github.com/UnimationKorea/personal
- ⚠️ **wrangler CLI 배포 실패**: API 토큰 권한 부족
- ✅ **대안 방법**: GitHub 연동 자동 배포 권장

## 🎯 권장 배포 방법: GitHub 연동

### 1. Cloudflare Dashboard 접속
1. [Cloudflare Dashboard](https://dash.cloudflare.com) 로그인
2. 좌측 메뉴에서 **"Pages"** 선택

### 2. 새 프로젝트 생성
1. **"Create a project"** 버튼 클릭
2. **"Connect to Git"** 선택 (GitHub 연동)

### 3. GitHub 저장소 연결
1. **GitHub 계정 연결** (처음이면 인증 필요)
2. **저장소 선택**: `UnimationKorea/personal`
3. **브랜치**: `main`

### 4. 빌드 설정
```
프로젝트 이름: pbl-bible-prompt-builder
프로덕션 브랜치: main
빌드 명령어: npm run build
빌드 출력 디렉토리: dist
루트 디렉토리: /
```

### 5. 고급 설정 (선택사항)
- **Node.js 버전**: 18 또는 최신
- **환경 변수**: 필요시 추가

### 6. 배포 실행
1. **"Save and Deploy"** 클릭
2. 자동 빌드 및 배포 시작
3. 완료 후 생성된 URL 확인

## 🔧 대안 배포 방법

### 방법 1: 수동 파일 업로드
1. Cloudflare Pages → **"Upload assets"** 선택
2. `dist/` 폴더의 `index.html` 파일 업로드
3. 프로젝트명: `pbl-bible-prompt-builder`

### 방법 2: CLI 권한 수정
현재 API 토큰에 다음 권한이 필요합니다:
- ✅ `Zone:Zone:Read`
- ❌ `User:User Details:Read` (누락)
- ❌ `Account:Cloudflare Pages:Edit` (확인 필요)

**권한 수정 방법**:
1. [Cloudflare API Tokens](https://dash.cloudflare.com/profile/api-tokens) 접속
2. 기존 토큰 편집 또는 새 토큰 생성
3. 필요한 권한 추가
4. 새 토큰으로 재배포 시도

## 📋 파일 구조 확인
현재 프로젝트 구조가 올바르게 설정되었습니다:
```
webapp/
├── dist/
│   └── index.html          # 배포될 파일
├── public/
│   └── index.html          # 소스 파일
├── package.json            # 의존성 및 빌드 스크립트
├── wrangler.jsonc          # Cloudflare 설정
└── README.md               # 프로젝트 문서
```

## 🎯 예상 결과
배포 완료 후:
- **Production URL**: `https://pbl-bible-prompt-builder.pages.dev`
- **Branch URL**: `https://main.pbl-bible-prompt-builder.pages.dev`

## 🛠️ 문제 해결

### 빌드 오류 시
```bash
# 로컬에서 빌드 테스트
npm run build

# 의존성 재설치
npm ci
```

### 배포 실패 시
1. GitHub 저장소 접근 권한 확인
2. 빌드 로그 확인
3. wrangler.jsonc 설정 검토

## ✅ 완료 체크리스트
- [x] GitHub 저장소에 코드 푸시
- [x] wrangler.jsonc 설정 완료
- [x] package.json 빌드 스크립트 설정
- [x] dist/ 디렉토리 빌드 성공
- [ ] Cloudflare Pages 프로젝트 생성
- [ ] GitHub 연동 설정
- [ ] 자동 배포 완료
- [ ] 프로덕션 URL 테스트

## 📞 지원
추가 도움이 필요하면 Cloudflare Pages 문서를 참조하세요:
- [Cloudflare Pages 문서](https://developers.cloudflare.com/pages/)
- [GitHub 연동 가이드](https://developers.cloudflare.com/pages/get-started/git-integration/)