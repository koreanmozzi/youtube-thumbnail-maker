# youtube-thumbnail-maker

유튜브 썸네일을 **"다크 시네마틱 + 단일 상징 오브제 + 감정·사건 메타포"** 문법으로 생성하는 Claude Code 스킬.
잘 만든 AI/IT 채널 썸네일을 분석해 정착시킨 디자인 언어를 일관되게 적용한다.

힉스필드(Higgsfield) **GPT Image 2**로 16:9 이미지를 뽑고, 브랜드 로고(클로드 선버스트·메타 인피니티·인스타 등)를
단순 나열이 아니라 *힘/캐릭터*로 배치한다. 텍스트·인물은 기본 제외하고, 한글 카피는 편집에서 오버레이하는 걸 권장한다.

## 핵심 디자인 문법 (4원칙)

1. **다크 시네마틱 배경** — 깊은 네이비-블랙, 비네팅, 드라마틱 림라이트.
2. **중앙 단일 히어로 오브제** — 시선 분산 없이 하나만 주인공으로.
3. **감정·사건 메타포** — 주제를 "사건"으로 번역(죽음/부활/대박/자동화 해방 등).
4. **브랜드 로고를 힘으로** — 로고가 빔을 쏘거나 부수는 등 능동적 역할.

## 설치

```bash
# 1. 클론
git clone https://github.com/koreanmozzi/youtube-thumbnail-maker.git

# 2. 스킬 폴더를 Claude Code 스킬 경로로 복사
#   macOS / Linux
cp -r youtube-thumbnail-maker/skills/youtube-thumbnail-maker ~/.claude/skills/
#   Windows (PowerShell)
Copy-Item -Recurse youtube-thumbnail-maker/skills/youtube-thumbnail-maker $env:USERPROFILE/.claude/skills/
```

## 사전 요구사항

- [Higgsfield CLI](https://github.com/higgsfield-ai/cli) 설치 및 로그인 (`higgsfield auth login`)
- `higgsfield-generate` 스킬(GPT Image 2 호출)이 함께 있으면 좋음

## 사용법

Claude Code에서 자연어로 요청한다.

**기존 썸네일 재생성** — 참고 이미지를 주고:
> "이 썸네일 학습한 문법으로 다시 만들어줘. 아이콘은 클로드·메타·인스타야."

**처음부터 생성** — 핵심 메시지 한 줄만 주면 됨:
> "썸네일 만들어줘. 메시지는 '클로드+메타로 의류 쇼핑몰 매출 10배', 아이콘은 클로드·메타·인스타."

자세한 요청 양식과 감정→메타포 사전은 [SKILL.md](skills/youtube-thumbnail-maker/SKILL.md) 참고.

## 라이선스

MIT
