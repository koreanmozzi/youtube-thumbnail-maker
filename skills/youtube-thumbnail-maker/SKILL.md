---
name: youtube-thumbnail-maker
description: >
  유튜브 썸네일을 "다크 시네마틱 + 단일 상징 오브제 + 감정·사건 메타포" 문법으로
  생성한다. 힉스필드 GPT Image 2로 16:9 이미지를 뽑고, 브랜드 로고(클로드 선버스트·
  메타 인피니티·인스타 등)를 힘/원천으로 배치한다. 텍스트·인물은 기본 제외(편집에서 오버레이).
  "썸네일 만들어줘", "썸네일 다시 만들어", "이 썸네일 재생성", "유튜브 썸네일 디자인",
  "AI 썸네일", "thumbnail" 같은 요청에 사용.
---

# YouTube Thumbnail Maker

기존에 잘 만든 채널(AI/PPT 다루는 채널)의 썸네일 문법을 학습해 정착시킨 스킬.
임팩트 있는 유튜브 썸네일을 일관된 디자인 언어로 생성한다.

## 핵심 디자인 문법 (반드시 지킬 4원칙)

1. **다크 시네마틱 배경** — 깊은 네이비-블랙, 비네팅, 드라마틱 림라이트. 화면 캡처/밝은 배경 금지.
2. **중앙 단일 히어로 오브제** — 시선 분산 요소 없음. 오브제 하나만 주인공으로.
3. **감정·사건 메타포** — 주제를 "사건"으로 번역한다. 설명하지 말고 *사건을 보여준다*.
4. **브랜드 로고를 힘/캐릭터로** — 로고가 빔을 쏘거나, 부수거나, 부활하는 등 능동적 역할. 단순 나열 금지.

부가:
- **텍스트·인물 기본 제외.** 핵심 카피(한글)는 이미지 생성이 불안정하므로 **편집에서 오버레이**. (사용자가 명시 요청 시만 포함)
- 황금 입자·잔불·갓레이(god ray)로 화려함 보강하되 **과하지 않게**(넓은 다크 여백 유지).

## 감정 → 메타포 사전 (학습된 매핑)

주제의 감정을 아래 사건으로 번역한다.

| 감정/메시지 | 시각 사건(메타포) |
|---|---|
| 죽음·종말·끝장 | 장례식 제단 / 비석 / 오브제가 산산조각 / 부서지는 삽·곡괭이(노가다 끝) |
| 부활·생존·복귀 | 땅에서 솟는 고대 유물 / 잿더미에서 재점화 |
| 대박·폭발적 성공 | 황금 폭발 + 우상향 상승 화살표(매출 급등) + 돈·코인 분출 |
| 압도·최강 | 신·거대 석상 / 르네상스 유화(자유의 여신상 패러디) |
| 의심·반전 | "이게 진짜?" 톤의 일상 오브제 클로즈업(약병 등) |
| 자동화·해방 | 수작업 도구(삽·체인)가 끊기거나 부서짐 + 자동화 힘이 대체 |

## 브랜드 로고 정확 묘사 (프롬프트에 그대로 사용)

- **클로드(Anthropic Claude)**: "a flat coral-orange sunburst / starburst symbol made of about twelve straight radiating spokes of varying length emanating from a single center point, clean geometric vector spark/asterisk shape, warm coral-orange, rendered as a glowing rounded-square app icon." ※ "빛 입자"로 묘사하면 형태가 뭉개짐 — 반드시 **방사형 스포크 별꼴**로 못 박을 것.
- **메타(Meta)**: "a smooth glossy blue infinity ribbon, interlocking double-loop infinity symbol, gradient electric blue, glowing."
- **인스타그램**: "a rounded-square camera icon with purple-pink-orange gradient, glowing."
- 다른 도구도 같은 식으로 형태를 구체 명시(색·실루엣·아이콘 형태).

## 두 가지 요청 모드

### 모드 A — 기존 썸네일 재생성 (지금까지의 방식)
사용자가 참고 썸네일 이미지를 주고 "이 느낌으로 다시" 요청.
1. 원본을 분석: 아이콘 정체 / 메시지 / 감정.
2. 4원칙으로 재해석해 단일 메타포로 압축.
3. 생성 → 전달 → 미세조정 옵션 2~3개 제시.

### 모드 B — 최초 생성 (참고 이미지 없음)
아래 **요청 양식**을 받아서 만든다. 빠진 항목은 한 번에 몰아 묻지 말고, **합리적 기본값으로 채우고 1개만** 확인.

```
[썸네일 요청 양식]
1. 영상 핵심 메시지 (한 줄)      예) "클로드+메타로 의류 쇼핑몰 매출 10배"
2. 등장 아이콘/브랜드            예) 클로드, 메타, 인스타  (없으면 생략)
3. 핵심 감정/사건               예) 대박 / 종말 / 부활 / 자동화 해방  (모르면 메시지에서 추론)
4. 중앙 오브제 (선택)           예) 마네킹+티셔츠 / 쇼핑백 / 부서지는 삽  (없으면 메시지에서 도출)
5. 텍스트·인물 포함 여부         기본: 둘 다 제외
6. 비율                        기본: 16:9
```

최소 입력은 **1번(핵심 메시지)** 하나. 나머지는 감정→메타포 사전으로 자동 도출 가능.

## 생성 파이프라인

힉스필드 GPT Image 2 사용 (`higgsfield-generate` 스킬과 동일 CLI).

```bash
# 0. 인증 확인 (실패 시 사용자에게 `higgsfield auth login` 요청)
higgsfield account status

# 1. 생성 (백그라운드 권장)
higgsfield generate create gpt_image_2 \
  --prompt "<아래 템플릿으로 조립한 영문 프롬프트>" \
  --aspect_ratio 16:9 --resolution 2k --wait
```

생성 후:
- 결과 URL을 `curl`로 내려받아 `CLAUDE-OUTPUTS/thumbnails/<주제슬러그>/<주제>_v<N>.png`에 저장.
- 같은 주제 재생성 시 **버전 번호 올림**(덮어쓰기 금지, 이력 보존).
- Read로 확인 후 `SendUserFile`로 전달.

## 프롬프트 템플릿 (영문, 이걸로 조립)

```
YouTube thumbnail, ultra cinematic, dark dramatic moody background, hyper-realistic 3D render,
high contrast, deep dark navy-black background with subtle vignette, moody premium look.
SINGLE CENTER HERO OBJECT: <중앙 오브제 + 감정 사건 메타포를 동사로 묘사>.
<BRAND EMBLEM 배치: 위 "브랜드 로고 정확 묘사"를 좌/우에 두고, 능동적 역할(빔·부수기·부활) 부여>.
Volumetric god rays, dramatic rim lighting, floating embers and golden sparkles,
lots of dark negative space, restrained elegant composition.
NO text, NO letters, NO words, NO human faces, NO people.
Epic impactful viral thumbnail aesthetic, octane render, 8k.
```

조립 규칙:
- 오브제는 **명사 하나 + 사건 동사**로(예: "a worn shovel SNAPPING and SHATTERING into golden light").
- 로고는 **충돌·인과**가 보이게(예: 클로드가 빔으로 삽을 부순다 / 두 로고의 빔이 오브제에 수렴해 폭발).
- "과함" 방지: 돈·코인·파티클은 "a few", "restrained", "lots of dark negative space"로 절제.
- 텍스트 포함 요청 시에만 NO text 줄을 빼고, 짧은 영문/숫자만(한글은 여전히 오버레이 권장).

## 전달 후 항상 제시할 것
1. 저장 경로(마크다운 링크).
2. **한글 카피는 편집 오버레이 권장** 안내(필요 시).
3. 미세조정 옵션 2~3개(오브제 교체 / 충돌 강조 / 화살표·방향선 추가 등).

## 참고
- 학습 출처: AI·PPT 다루는 유튜브 채널 썸네일 9종 분석 + 사용자 피드백 반복.
- 과거 산출물: `CLAUDE-OUTPUTS/thumbnail-claude-meta/`(클로드×메타 의류 쇼핑몰, 광고 노가다 끝 케이스).
