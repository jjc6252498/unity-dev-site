# Unity Dev Site

Vue.js로 제작된 Unity 개발 소개 웹사이트입니다.

## 로컬 개발

```bash
npm install
npm run dev
```

## 빌드

```bash
npm run build
```

## 배포 방법

### Vercel로 배포하기

1. [Vercel](https://vercel.com) 접속 및 회원가입
2. "Add New Project" 클릭
3. GitHub 저장소 연결 또는 프로젝트 업로드
4. Framework Preset: `Vite` 선택
5. Deploy 버튼 클릭

### Netlify로 배포하기

1. [Netlify](https://netlify.com) 접속 및 회원가입
2. "Add new site" → "Deploy manually" 클릭
3. `dist` 폴더를 드래그 앤 드롭
4. 배포 완료!

또는 GitHub 연동:
1. GitHub에 저장소 생성 및 푸시
2. Netlify에서 "Import from Git" 선택
3. Build command: `npm run build`
4. Publish directory: `dist`
