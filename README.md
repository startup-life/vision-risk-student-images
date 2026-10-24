# vision-risk-student-images

품질관리·산업안전 실습용 합성 이미지 210장과 파일 목록입니다. Teachable Machine 학습과 사진 선택 실습에 쓰는 사진을 모았습니다.

## 이 사진은 무엇인가

- 생성형 AI로 만든 합성 이미지입니다. 실제 공장이나 실제 사람의 사진이 아닙니다.
- 1024x1024 PNG이고 전체 약 162MiB(170MB)입니다. 파일당 최대 약 1.5MB입니다.
- 품질관리 105장과 산업안전 105장입니다.

| 용도 | 품질관리 | 산업안전 | 합계 |
|---|---:|---:|---:|
| 학습 준비용 (`train`) | 90 | 90 | 180 |
| 결과 확인용 (`val`) | 15 | 15 | 30 |

## 폴더

| 경로 | 내용 |
|---|---|
| `assets/dataset/images/` | 사진 210장 (`Q-IND-###.png`, `S-IND-###.png`) |
| `metadata/generation_manifest.csv` | 사진별 트랙, 용도, 경로, SHA-256 |

**학습 준비용·결과 확인용 사진은 파일 목록의 `split` 열로 구분합니다.** `train`은 학습용, `val`은 검증용입니다.

[파일 목록](metadata/generation_manifest.csv)을 열면 아래와 같은 행이 있습니다. 실제 파일 중 두 장을 골라 필요한 열만 옮겼습니다.

| `image_id` | `track` | `split` | 실습에서 할 일 |
|---|---|---|---|
| `Q-IND-001` | `quality` | `train` | `Q-IND-001.png`를 모델 학습에 사용 |
| `Q-IND-023` | `quality` | `val` | `Q-IND-023.png`는 학습에 넣지 않고, 학습 후 판정 결과 확인에 사용 |

두 사진은 모두 품질관리(`quality`) 자료입니다. 같은 폴더에 있어도 `split` 값에 따라 사용하는 단계가 다릅니다.

사진을 찾을 때는 같은 행의 `filename` 열을 봅니다. 위 두 파일의 실제 위치는 다음과 같습니다.

- 학습용: [assets/dataset/images/Q-IND-001.png](assets/dataset/images/Q-IND-001.png)
- 검증용: [assets/dataset/images/Q-IND-023.png](assets/dataset/images/Q-IND-023.png)

사진은 모두 `assets/dataset/images/`에 있습니다. `train`·`val`이라는 별도 폴더는 없습니다.

`subtype` 열은 비어 있습니다. 사진별 유형은 학생용 저장소에 넣지 않습니다.

Test 사진은 이 저장소에 없습니다. 매니페스트의 `split`이 `test`인 행에는 대응하는 이미지 파일이 포함되지 않습니다.

## 실습에서 쓰는 방법

공장 품질 사진으로 정상·불량을 구분하는 응용 과제에 사용합니다.

준비 순서와 사진을 나누는 기준은 교재에서 확인합니다. 강사가 제공한 ‘텀블러 외관 불량 판정하기’의 사용 방법 8)을 따릅니다.

이 과제에서는 파일 목록의 `track`이 `quality`인 사진을 고릅니다. `split`이 `train`인 90장으로 학습하고 `val`인 15장으로 결과를 확인합니다.

`safety` 사진 105장은 별도의 산업안전 실습용입니다.

품질 기준서는 포함되어 있지 않습니다. 실습에 사용할 품질 기준서는 교재의 안내에 따라 따로 준비합니다.

## 받는 방법

`git clone`으로 받습니다. ZIP으로 받지 않습니다.

사진은 일반 파일이라 Git LFS가 필요 없습니다. 약 170MB를 받으므로 회선에 따라 시간이 걸립니다.

### Windows

1. Git for Windows가 설치돼 있는지 PowerShell에서 확인합니다.

```powershell
git --version
```

2. 실습 폴더로 이동해 clone합니다. 폴더 위치는 교재의 안내를 따릅니다.

```powershell
git clone https://github.com/startup-life/vision-risk-student-images.git
```

### macOS

터미널에서 같은 `git clone` 명령을 실행합니다.

## 파일이 온전한지 확인

`metadata/generation_manifest.csv`의 `sha256` 값과 받은 파일의 해시가 같으면 온전한 파일입니다. PowerShell 예시입니다.

```powershell
Get-FileHash vision-risk-student-images\assets\dataset\images\Q-IND-001.png -Algorithm SHA256
```

## 이용 범위

이용 조건은 아직 정해지지 않았습니다. 정해지면 이 절과 `LICENSE` 파일을 채웁니다.

그 전에는 수강 실습 목적으로만 사용하고 다시 배포하지 않습니다.
