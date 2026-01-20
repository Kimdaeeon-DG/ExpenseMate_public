# 일일경비 관리 시스템

회사 경비 신청 및 관리를 위한 웹 애플리케이션입니다. 사원들이 모바일로 쉽게 경비를 신청하고, 관리자가 효율적으로 승인하고 권한을 관리할 수 있습니다.

## 🌟 주요 기능

### 사원 기능 (PWA 모바일 최적화)
- **경비 신청**: 위치, 금액, 이동거리, 톨비, 영수증 첨부
- **자동 분류**: 이동거리 입력 여부에 따른 업무비/식비 자동 분류
- **신청 내역**: 미처리/처리완료 내역 조회
- **프로필 관리**: 이름, 회사코드 설정

### 관리자 기능 (데스크톱 최적화)
- **대시보드**: 달력 기반 경비 현황 조회
- **승인 관리**: 경비 승인/반려 처리, 검색 및 필터링
- **권한 관리**: 사용자 권한 변경, 신규 가입자 승인

## 🛠 기술 스택

- **Frontend**: Next.js 15 (App Router), TailwindCSS, TypeScript
- **Backend**: Supabase (PostgreSQL, Auth, Storage)
- **State Management**: Zustand
- **Authentication**: OAuth (Google, Kakao, Naver)
- **UI Components**: Heroicons, React Hook Form
- **Deployment**: Vercel

## 🚀 시작하기

### 1. 프로젝트 클론 및 의존성 설치

```bash
git clone <repository-url>
cd expense-management
npm install
```

### 2. 환경 변수 설정

`env.example` 파일을 참고하여 `.env.local` 파일을 생성하고 설정:

```bash
cp env.example .env.local
```

필요한 환경 변수:
- `NEXT_PUBLIC_SUPABASE_URL`: Supabase 프로젝트 URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`: Supabase Anonymous Key
- `SUPABASE_SERVICE_ROLE_KEY`: Supabase Service Role Key

### 3. Supabase 설정

1. [Supabase](https://supabase.com)에서 새 프로젝트 생성
2. `supabase-schema.sql` 파일의 내용을 SQL Editor에서 실행
3. Authentication > Providers에서 OAuth 설정:
   - Google OAuth
   - Kakao OAuth (추가 설정 필요)
   - Naver OAuth (추가 설정 필요)
4. Storage에서 `receipts` 버킷 생성 및 정책 설정

### 4. 개발 서버 실행

```bash
npm run dev
```

[http://localhost:3000](http://localhost:3000)에서 애플리케이션을 확인할 수 있습니다.

## 📱 PWA 설정

이 애플리케이션은 PWA(Progressive Web App)로 구성되어 있어 모바일 기기에 설치할 수 있습니다:

1. 모바일 브라우저에서 사이트 접속
2. "홈 화면에 추가" 선택
3. 네이티브 앱처럼 사용 가능

## 🔐 권한 체계

| 역할 | 접근 권한 | 기능 |
|------|-----------|------|
| 최고 관리자 | 모든 페이지 | 모든 권한 관리 가능 |
| 관리자 | 관리자/사원 페이지 | 승인 관리, 권한 조회만 가능 |
| 사원 | 사원 페이지만 | 경비 신청 및 내역 조회 |
| 미승인 | 프로필만 | 관리자 승인 대기 |

## 📂 프로젝트 구조

```
src/
├── app/                    # Next.js App Router
│   ├── admin/             # 관리자 페이지
│   ├── employee/          # 사원 페이지
│   └── auth/              # 인증 관련
├── components/            # 재사용 컴포넌트
├── lib/                   # 유틸리티 함수
│   ├── supabase.ts       # Supabase 클라이언트
│   └── auth.ts           # 인증 관련 함수
└── store/                 # Zustand 상태 관리
```


## 🌐 배포

### Vercel 배포

1. GitHub에 프로젝트 푸시
2. [Vercel](https://vercel.com)에서 프로젝트 import
3. 환경 변수 설정
4. 배포 완료

### 환경 변수 설정 (배포용)

배포 시 다음 환경 변수들을 설정해야 합니다:
- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`

## 📋 사용 가이드

### 초기 설정

1. **최고 관리자 설정**: `supabase-schema.sql`에서 초기 관리자 이메일 설정
2. **회사 코드 설정**: 사원 가입 시 사용할 회사 코드 정의
3. **OAuth 설정**: 각 소셜 로그인 제공업체에서 클라이언트 ID/Secret 발급

### 사원 사용법

1. 소셜 로그인으로 가입
2. 프로필에서 이름과 회사 코드 입력
3. 관리자 승인 대기
4. 승인 후 경비 신청 가능

### 관리자 사용법

1. 대시보드에서 월별 경비 현황 확인
2. 승인 관리에서 경비 승인/반려 처리
3. 권한 관리에서 사용자 권한 변경

## 🔧 개발 정보

### 주요 라이브러리

- `@supabase/supabase-js`: Supabase 클라이언트
- `@heroicons/react`: 아이콘 컴포넌트
- `react-hook-form`: 폼 관리
- `react-hot-toast`: 토스트 알림
- `date-fns`: 날짜 처리
- `zustand`: 상태 관리

### 코드 스타일

- TypeScript 사용
- ESLint + Prettier 설정
- Tailwind CSS 유틸리티 클래스

## 📞 지원

문제가 발생하거나 기능 요청이 있으시면 이슈를 등록해 주세요.

## 📄 라이선스

MIT License
