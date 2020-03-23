# Git bash 명령어

> 현재 깃 사용자 아이디 등록.

```bash
git config --global user.name "kdseol"
```
> 현재 깃 사용자 이메일 등록.

```bash
git config --global user.email "kdseol@urpsys.com"
```

> 만약 프로젝트마다 user.name과 user.email을 다르게 하고 싶다면,

```bash
git config --local user.name "kdseol"
git config --local user.email "seolkd.e@gmail.com"
```


```
> 개행문자 문제 해결.

```bash
git config --global core.autocrlf true(Windows)
git config --global core.autocrlf input(Linux/Mac)
```
> gitAddress(프로젝트주소)에서 프로젝트 다운로드(복사)

```bash
git clone gitAddress.git
```
> 현재 상태 확인.

```bash
git status 
```
> 모든 변경사항 적용.

```bash
git add . 
```
> 메세지를 포함해 커밋.

```bash
git commit -m "message"
```
> 서버로 푸시

```bash
git push
```


## 새로 레파지토리를 생성할 때

GitHub에서 Repository를 생성한 후

bash에서 똑같이

```bash
 git push --set-upstream [GitHub Address]

```