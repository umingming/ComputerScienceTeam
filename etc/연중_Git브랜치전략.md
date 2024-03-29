# 주제: Git 브랜치 전략

### Git 브랜치는 무슨 용도인가?

개발을 진행할 때, 대부분의 개발은 팀 단위로 진행된다. 팀 단위의 개발에서 여러 사람이 다양한 작업을 동시에 진행할 수 있게 해주는 기능이 Git Branch다.  
Git에서 제일 기본적인 브랜치는 master 브랜치로, master 브랜치를 기준으로 다른 브랜치를 생성하여 작업 후 다시 master에 병합하는 식으로 보편적인 개발을 진행한다.

<br>
<br>

### 이런 Git 브랜치가 여러 전략이 있다구요??

이번 주제에서 일반적으로 많이 알려진 브랜치 전략을 소개하고자 한다.

1. Git-Flow
2. Github-Flow
3. Gitlab-Flow

각각의 브랜치 전략마다 장, 단점이 존재하며 프로젝트의 성격이나 개발 방식을 고려하여 선택하면 좋을 것 같다.

<br>
<br>

### Git-Flow

![gitflow](https://user-images.githubusercontent.com/93513959/200131751-7b3efd4e-1c03-49e7-b6d6-269743058a23.png)


Git Flow는 `feature`, `develop`, `release`, `hotfix`, `master` 총 다섯 가지의 브랜치를 가지는 전략이다.  
각 브랜치의 역할을 알아보자.

<br>

##### feature

feature는 기능 단위로 생성하는 브랜치다.  
어떤 한 기능에 대한 개발을 진행하고 `develop`에 merge한다.

##### develop

develop 브랜치는 개발을 진행하는 용도의 브랜치다.
여러 feature 브랜치가 모여 develop 브랜치가 형성된다.  
개발이 완료되면 배포를 위해 release에 merge한다.

##### release

release 브랜치는 develop 브랜치를 배포하기 위해 준비하는 과정을 가지는 브랜치다.  
release 브랜치에서는 기능적 버그와 수정 및 개선사항을 점검한다.  
모든 준비를 마치고 master 및 develop에 merge한다.

##### hotfix

hotfix 브랜치는 배포 후 버그가 발생할 경우, 버그에 대한 처리를 하는 브랜치다.  
master를 기준으로 생성하며, 버그가 픽스되면 develop 브랜치 및 release 브랜치, master 브랜치에 merge한다.

##### master

master 브랜치는 최종적으로 배포된 소스코드를 가지는 브랜치다.

#### Git Flow의 장단점

장점: 각 용도별로 세분화되어 있다. 세분화되어 있기 때문에 큰 규모의 프로젝트에서 이점이 있다.  
단점: 흐름이 복잡하다. CI/CD를 적용하기 비교적 힘들다.

<br>
<br>

### Git-hub Flow

![githubflow](https://user-images.githubusercontent.com/93513959/200131758-9cf71e95-8d12-49c5-8fb2-97528bdd8f68.png)

github flow의 과정은 다음과 같다.

1. master 브랜치에서 개발이 시작된다.
2. 기능 구현이나 버그가 발생하면 issue를 작성한다.
3. 팀원들이 issue 해결을 위해 master 브랜치에서 생성한 feature/{구현기능} 브랜치에서 개발을 하고 commit log를 작성한다.
4. push를 하면 pull request를 날릴 수 있다.
5. pull request를 통해 팀원들 간의 피드백, 버그 찾는 과정이 진행된다. release 브랜치가 없으므로 이 과정이 탄탄하게 진행되어야 한다.
6. 모든 리뷰가 이루어지면, merge하기 전에 배포를 통해 최종 테스트를 진행한다.
7. 테스트까지 진행되면 master 브랜치에 머지한다.

오직 master 브랜치와 feature 브랜치를 중점적으로 사용한다.

### Git hub Flow의 장단점

장점: 단순하다. pull request 기능을 사용하도록 권장을 하며 수시로 배포가 발생하므로 CI/CD가 자동화 되어 있는 환경에서 사용하기 좋다.

단점: pull request에서 팀원간의 충분한 리뷰와 피드백이 진행되지 않으면 배포된 자체에서 버그가 발생할 수 있다.

<br>
<br>

### GitLab-Flow

![image](https://user-images.githubusercontent.com/93513959/200131781-fbb73f0a-5f3d-4448-9f98-b99f2b2642e8.png)

GitLab Flow는 `feature`, `master`, `production`, `pre-production` 브랜치를 가진다.

각 브랜치의 역할을 알아보자.

<br>

##### feature

feature는 기능 단위로 생성하는 브랜치다.  
master에서 분기되고 marge됨.

##### master

git flow의 develop 브랜치와 동일한 역할로, feature에서 기능 구현하고 master에 marge하고 그 기능에 대해 test하는 분기.  
테스트를 통과하고 검증되었다면 production로 marge.  
만약 staging 단계를 원한다면 pre-production 브랜치로 marge.

##### production

git flow의 master 브랜치와 동일한 역할로, 배포하기 위한 브랜치.

##### pre-production

기존 master와 production에 pre-production을 둬서 개발 내용을 천천히 테스팅할 수 있는 브랜치.  
즉, Production 브랜치에서 릴리즈된 코드가 항상 프로젝트의 최신 버전 상태를 유지할 필요가 없음.

### GitLab-Flow 장단점

Git과 Github의 중간 단계의 단순함이다. GitLab 같은 경우에는 pre-production 브랜치를 통해 배포 버전을 미리 준비할 수 있다는 것이 장점이 될 것 같다.

<br>
<br>
<br>
<br>

### 출처

https://backlog.com/git-tutorial/kr/stepup/stepup1_1.html  
https://about.gitlab.com/topics/version-control/what-is-gitlab-flow/  
https://docs.github.com/en/get-started/quickstart/github-flow  
https://brownbears.tistory.com/605  
https://gyoogle.dev/blog/github/Git%20vs%20GitHub%20vs%20GitLab%20Flow.html

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]: https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
