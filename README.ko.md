# 자기소개 타이머

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

동창회 등에서 참가자가 순서대로 자기소개를 할 때 쓰는 한 페이지짜리 타이머입니다. 브라우저에서 `index.html`을 열기만 하면 됩니다. 설치, 서버, 인터넷 연결이 필요 없습니다.

## 사용 방법

1. 브라우저(Safari / Chrome)에서 `index.html`을 엽니다.
2. 설정 화면에서 CSV를 불러오고(`sample/participants.csv` 또는 “샘플 불러오기”), 사람별 출석 여부를 바꾸고, 원하는 필드로 정렬하고, 제목 / 1인당 시간 / 호칭 / 언어를 설정한 뒤 소리를 테스트합니다.
3. “타이머로 이동”을 누릅니다(이때 소리도 활성화됩니다).
4. 타이머를 진행합니다:

| 조작 | 동작 |
|---|---|
| `Space` / 시작 버튼 | 다음 사람 시작(박수 소리) |
| 오른쪽 목록의 이름 클릭 | 그 사람부터 시작. 앞 순서였던 사람은 “건너뛴 사람”으로 이동 |
| “건너뛴 사람”의 이름 클릭 | 그 사람 시작 |
| “건너뛴 사람”의 “출석” 체크 해제 | 확인 후 결석 처리하고 목록에서 제거(타이머는 멈추지 않음) |

남은 시간 10초: 1초마다 틱 소리 · 3초: 빠른 삐삐 소리 · 0초: 폭발음과 “시간 종료” 라벨. 오른쪽 위에 전체 경과 시간, 오른쪽 열에 다음 10명이 표시됩니다.

## CSV 형식

첫 행은 머리글입니다. UTF-8 / Shift_JIS를 자동 감지합니다. 이름과 호칭 열은 머리글(예: `이름`, `호칭`)로 자동 선택되며 설정에서 바꿀 수 있습니다. 호칭 칸이 비어 있으면 기본 호칭을 사용합니다.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## 다국어

16개 언어를 지원합니다. 설정 화면의 “언어”에서 바꿉니다(처음에는 브라우저 언어를 사용하고, 선택한 언어는 저장됩니다). 화면 문구, 제목 기본값, 기본 호칭, 샘플 데이터, 호칭 위치(이름 앞/뒤)가 언어에 맞게 바뀌며, 아랍어는 오른쪽에서 왼쪽 레이아웃을 사용합니다. 번역은 원어민 검수를 거치지 않았습니다. 수정은 `index.html`의 `I18N`을 편집하세요. 언어를 추가하려면 `LANGS`, `I18N`, `SAMPLE_NAMES`에 항목을 하나씩 추가하세요.

## 모바일

세로·가로 방향 휴대폰 레이아웃을 지원합니다. iPhone에서는 무음 스위치가 켜져 있으면 소리가 나지 않습니다. 파일은 “파일” 앱으로 여는 것이 가장 확실하며, GitHub Pages로 공개하면 URL만 열면 됩니다.

## 구성

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
```

`index.html` 하나에 모든 것이 들어 있습니다: 언어 사전, CSV 파서, 설정 화면, Web Audio 효과음 합성(오디오 파일 불필요), 타이머 로직(시각 기반이라 오차가 쌓이지 않음), 진행 화면. 설정과 진행 상황은 `localStorage`에 자동 저장됩니다.

라이선스: 미지정
