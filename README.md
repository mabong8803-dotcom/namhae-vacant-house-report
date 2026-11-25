# namhae-vacant-house-report

남해군 농촌소멸대응 빈집재생사업 정책분석보고서의 선행연구·인용 검증 작업 저장소.

## 포함 도구

| 경로 | 도구 | 용도 | 라이선스 |
|---|---|---|---|
| `tools/CheckIfExist` | [CheckIfExist](https://github.com/zabbonat/References-Validation) | 참고문헌을 CrossRef·Semantic Scholar·OpenAlex·DBLP·arXiv와 대조해 실존 여부 확인. PDF/DOCX 일괄 처리 가능 | MIT |
| `tools/HalluCiteChecker` | [HalluCiteChecker](https://github.com/yusuke1997/HalluCiteChecker) | 논문 PDF의 인용을 추출해 환각 인용 탐지 | Apache-2.0 |

두 도구는 git submodule로 원본 저장소를 참조합니다(코드 복사 아님).

```bash
git clone --recurse-submodules https://github.com/mabong8803-dotcom/namhae-vacant-house-report.git
```

이미 받은 경우:

```bash
git submodule update --init --depth 1
```

## 사용법

### CheckIfExist (설치 없이 가장 쉬움)

웹 버전: https://zabbonat.github.io/References-Validation/ 에 보고서 .docx를 올리면 참고문헌을 일괄 검증합니다.
로컬 실행·MCP 서버 사용법은 `tools/CheckIfExist/README.md` 참고.

### HalluCiteChecker

```bash
python3.12 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
hallucitechecker -i report.pdf
```

- 입력은 **PDF**입니다. .docx는 PDF로 변환 후 사용하세요.
- 첫 실행 때 인용 추출 모델을 내려받으므로 인터넷 연결이 필요합니다.

## 한계 (중요)

- **국내 문헌은 대부분 검증되지 않습니다.** HalluCiteChecker의 기본 DB는 ACL Anthology·arXiv·DBLP(컴퓨터과학 중심)이고, CheckIfExist도 DOI가 없는 KCI 논문은 "Not Found"로 나올 수 있습니다. 국내 학술지는 [KCI](https://www.kci.go.kr)·[RISS](https://www.riss.kr)에서 직접 대조하세요.
- 신문기사·보도자료·법령은 두 도구의 검증 대상이 아닙니다. 원문 링크와 [국가법령정보센터](https://www.law.go.kr)로 확인하세요.

## 선행연구 수집 (참고)

[rubato103/textmining_KCI_RISS](https://github.com/rubato103/textmining_KCI_RISS)(KCI·RISS 엑셀 기반 텍스트마이닝, R)는 현재 GitHub에서 접근되지 않아(비공개 또는 삭제 추정) 포함하지 못했습니다. 또한 학술·교육 목적 라이선스여서 재배포에 제약이 있습니다. 대신 RISS OpenAPI(https://www.riss.kr/openapi)와 KCI 검색결과 엑셀 내보내기를 이용하세요.
