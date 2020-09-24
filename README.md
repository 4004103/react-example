# react-example

**npm, npx, node.js 필수 설치!**

node.js는 구글에 검색해서 설치. (npm이랑 같이 설치되기때문에 npm은 별도로 설치 안해도 됨)

`node -v`, `npm -v`, `npx -v`으로 버전 확인 가능.

`git --version`으로 깃 버전 확인 가능.

```bash
npm install npx -g // npx를 글로벌로 설치.
```


# creat-react-app
React Web App을 Set up 할 수 있게 도와줌.

```bash
// iterm에서 실행
cd Documents // 내 문서에서

npx creap-react-app project_name // 리액트 설치

npm start // vscode 해당 프로젝트 터미널에서 실행 -> 서버 실행
```

# github에 리포지토리 생성
```bash
// vscode 터미널에서 실행. ~/Documents/project_name/ 확인하고,
git init
```
깃허브로 가서 리포지토리 생성. (packge.json 에 있는 name으로 하는게 편함)

리포지토리 url이 생성되면 

```bash
git remote add origin 리포지토리 url 붙여넣기.

git add

git commit -m 첫번째 커밋 내용

git push origin master
```

그리고 깃헙에서 새로고침하면 리포지토리에 복사되어있음.



