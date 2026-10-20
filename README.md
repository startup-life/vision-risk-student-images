# vision-risk-student-images

현장 리스크 실습용 이미지 210장과 매니페스트입니다. Teachable Machine 학습과 사진 선택 실습에 쓰는 사진만 모았습니다.

## 이 사진은 무엇인가

- 생성형 AI로 만든 합성 이미지입니다. 실제 공장이나 실제 사람의 사진이 아닙니다.
- 1024x1024 PNG이고 전체 약 162MiB(170MB)입니다. 파일당 최대 약 1.5MB입니다.
- 품질관리 105장과 산업안전 105장입니다.

| 용도 | 품질관리 | 산업안전 | 합계 |
|---|---:|---:|---:|
| Train (학습) | 90 | 90 | 180 |
| Val (검증) | 15 | 15 | 30 |

## 폴더

| 경로 | 내용 |
|---|---|
| `assets/dataset/images/` | 사진 210장 (`Q-IND-###.png`, `S-IND-###.png`) |
| `metadata/generation_manifest.csv` | 사진별 트랙, 용도, 유형, 경로, SHA-256 |

`subtype` 열이 사진의 유형입니다. 학습과 검증에 쓰는 유형 이름입니다.
Test 사진은 이 저장소에 없습니다. 매니페스트의 `split`이 `test`인 행은 파일 없이 해시만 있습니다.

## 받는 방법

`git clone`으로 받습니다. ZIP으로 받지 않습니다. 사진은 일반 파일이라 Git LFS가 필요 없습니다. 약 170MB를 받으므로 회선에 따라 시간이 걸립니다.

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
그 전에는 수강 실습 목적으로만 사용하고, 다시 배포하지 않습니다.
