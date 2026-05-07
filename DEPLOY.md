# GitHub 배포 가이드

이 문서는 `ai-era-advisor` 스킬을 본인의 GitHub 저장소(https://github.com/junghoonwoo-stack)에 올리는 방법입니다.

## 1단계: 저장소 만들기

GitHub에서 새 저장소를 만드세요:
- 저장소 이름: `ai-era-advisor` (권장)
- 공개 여부: Public (다른 사람이 쓸 수 있게)
- README, .gitignore, license 모두 **체크하지 마세요** — 이미 파일이 있습니다

## 2단계: 파일 다운로드

이 폴더의 모든 파일을 본인 컴퓨터에 다운로드하세요:
- `SKILL.md` (메인 스킬 정의)
- `README.md` (저장소 설명)
- `LICENSE` (MIT 라이선스)
- `.gitignore`
- `evals/evals.json` (테스트 케이스)
- `DEPLOY.md` (이 파일)

## 3단계: 터미널에서 푸시

다운로드한 폴더로 이동한 뒤:

```bash
cd ai-era-advisor

# Git 초기화
git init
git branch -M main

# 파일 추가
git add .
git commit -m "Initial commit: AI Era Advisor skill v1.0"

# 본인 저장소 연결 (URL은 본인 것으로 수정)
git remote add origin https://github.com/junghoonwoo-stack/ai-era-advisor.git

# 푸시
git push -u origin main
```

GitHub 인증을 요구하면 Personal Access Token을 사용하세요 (비밀번호 인증은 더 이상 지원 안 됨).

## 4단계: `.skill` 파일 만들기 (배포용)

다른 사람이 Claude.ai에서 바로 설치할 수 있도록 `.skill` 파일을 만들 수 있습니다:

```bash
# 폴더를 zip으로 압축한 후 확장자만 .skill로 변경
cd ..
zip -r ai-era-advisor.zip ai-era-advisor -x "*.git*" "DEPLOY.md"
mv ai-era-advisor.zip ai-era-advisor.skill
```

이 `.skill` 파일을 GitHub Releases에 올리면 사람들이 다운로드해서 Claude.ai에 바로 업로드할 수 있습니다.

## 5단계: README 다듬기 (선택)

저장소 첫 화면에서 보일 README는 이미 모바일 친화적으로 작성되어 있지만, 본인 톤에 맞게 수정해도 좋습니다. 특히:
- 상단 배지 (build status, license 등) 추가
- 실제 스크린샷 (Claude 앱에서 사용한 화면)
- 본인 SNS 링크

## 6단계: 홍보

스킬을 만들었으면 알려야 사용됩니다:
- 링크드인에 한글로 짧게 — "AI 시대 사업·교육 상담을 모바일에서 짧게 받을 수 있는 Claude Skill 만들었습니다" + 사용 예시 스크린샷 한 장
- 트위터/X 영문 버전
- 본인 블로그가 있다면 메이킹 스토리

## 업데이트 방법

스킬을 개선했을 때:

```bash
git add .
git commit -m "Update: [변경 내용 한 줄]"
git push
```

새 `.skill` 파일도 다시 만들어서 Releases에 v1.1 등으로 올리세요.

---

**팁**: `SKILL.md`의 `description` 필드는 Claude가 이 스킬을 언제 쓸지 결정하는 핵심이에요. 사용해보고 트리거가 잘 안 되면 description에 더 많은 트리거 문구를 추가하세요.
