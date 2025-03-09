# git push

## 1. git 초기화

프로젝트 폴더로 이동한 후, git 저장소를 초기화 한다.
```sh
cd /path/to/your/project # 프로젝트 폴더로 이동
git init # git 초기화
```

## 2. .gitignore 설정 (선택 사항)

node_modules 등 불필요한 파일을 git에 올리지 않으려면 .gitignore 파일을 생성한다.
```sh
echo "node_modules/" >> .gitignore
echo ".env" >> .gitignore # 환경 변수 파일도 제외 (필요한 경우)
```

## 3. git에 파일 추가 및 커밋

모든 파일을 git에 추가하고 커밋한다.
```sh
git add .
git commit -m "Initial commit"
```

## 4. github 또는 gitlab에 원격 저장소 생성

github 또는 gitlab에서 새로운 저장소(레포지토리)를 생성한다.

## 5. 원격 저장소 연결

새로 만든 github 저장소와 로컬 프로젝트를 연결한다.
```sh
git remote add origin ${git url}
```

## 6. github에 코드 푸시

로컬 커밋을 원격 저장소에 푸시한다.
```sh
git branch -M main  # 브랜치 이름을 main으로 설정 (필요시)
git push -u origin main  # 원격 저장소로 푸시
```

프로젝트가 github에 업로드 완료되었다.