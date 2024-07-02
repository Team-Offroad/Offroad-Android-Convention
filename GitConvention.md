## Branch Convention
- 기본적으로 [Git Flow](https://inpa.tistory.com/entry/GIT-%E2%9A%A1%EF%B8%8F-github-flow-git-flow-%F0%9F%93%88-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5) 전략을 활용한다.
  <img src="https://github.com/Team-WSS/WSS-Android-Convention/assets/114990782/050ed37b-bb15-46e2-933a-b840e35e9d5f" width="50%" height="50%"/>


- branch와 issue는 1:1 대응한다.
- 다음과 같은 브랜치를 사용한다.
    - feature: 기능 단위의 브랜치
        - 구현이 완료되면, develop 브랜치에 병합된다.
        - child-feature: 부모 feat 브랜치를 더 작게 분리한 브랜치
            - 구현이 완료되면, parent feat 브랜치에 병합된다.
            - 네이밍은 부모와 동일하게 feature를 사용한다.
    - develop: 여러 feat 브랜치가 병합된 브랜치
    - release: QA 단계에 사용할 MVP 버전의 브랜치
        - QA 제품에 코드 수정이 발생할 경우, feat - develop - release 순으로 재병합된다.
    - master: 실제 배포된 버전의 브랜치
        - 배포 제품에 버그가 발생할 경우, hotfix 브랜치를 통해 즉각 대응한다.
    - hotfix: 배포 제품의 버그 대응 브랜치
        - develop 브랜치와 master 브랜치에 모두 업데이트한다.

### Branch Naming
- 브랜치단위/이슈번호
    - 브랜치 단위
        - feature
        - develop
        - release
        - master
        - hotfix
- 브랜치 네이밍 예시는 다음과 같다.
    - 예시) `feature/1`


## Commit Convention
- 사용할 커밋 타입은 다음과 같다.
    - feature: 새로운 기능을 구현합니다. (변경 사항이 클 경우에도 이에 해당)
    - refactor: 기존 코드를 리팩토링합니다.
    - fix: 버그를 수정합니다.
    - build: 빌드 업무 및 패키지 매니저를 수정합니다.
    - docs: 문서 작업을 진행합니다.
- 커밋 메시지는 영어로 작성한다.
- 커밋 메시지의 첫 단어는 upper case로 작성한다.
- 마침표와 이슈 번호는 별도로 표기하지 않는다.
- 커밋 메시지 예시는 다음과 같다.
    - 예시) `feature: Add domain module`


## Issue Convention
- 제목에 사용할 prefix는 커밋 컨벤션에 사용하는 타입과 동일하다.
    - 해당 이슈의 주 역할에 맞게 설정한다.
- 이슈는 작은 범위의 기능 단위로 발행한다.
    - 해당 기능이 너무 클 경우 자식 이슈로 분리한다.
- 제목 예시는 다음과 같다.
    - 예시) `feature: Add domain module`

```markdown
<!-- 이슈 컨벤션 추가 예정 -->
```


## PR Convention
- 제목 예시 역시 이슈 제목과 같다.
    - 예시) `feature: Add domain module`

```markdown
<!-- PR 컨벤션 추가 예정 -->
```

### Reviewer Convention
- PR은 **24시간 내**로 리뷰를 한다.
- 각자 코드리뷰 달지 않은 PR이 **`5개 이상`** 일 경우 **모든 업무를 중단**하고 리뷰를 **최우선**으로 진행한다.
``` kotlin
Class WebsosoAndroidDeveloper() {
	var requirePR = 0

	if (requirePR >= MAX_NOT_REVIEWED_CODE_REVIEW_PR) {
		suspendDevelop()
		startReview()
	}
	
	companion object {
	   private const val MAX_NOT_REVIEWED_CODE_REVIEW_PR = 5
	}
}
```
- RCA 룰을 따른다.
    - **R**(equest Change) 무조건 반영해주세요
    - **C**(omment) 웬만하면 반영해주세요
    - **A**(pprove) 사견 / 칭찬 / etc
    - 예시 ) r: 그래들 컨벤션에서 feature의 의존성에 data가 없는 것 같습니다.


### Reviewee Convention
- 본인 PR의 **Description**은 리뷰어가 잘 이해할 수 있도록 **자세히 작성**한다.
- 코드 변경사항은 다음을 준수한다.
    - 권장 **100~300 (+)**, **맥시멈 500(+)**
- 최소 **1명에게 aprrove**를 받으면 머지할 수 있다.
- 리뷰가 끝나면, 리뷰이는 우선적으로 전체 코드 리뷰를 확인하고 reaction 한다.
    - 최소한 이모지라도 남길 것
- **빠르게 리뷰가 필요**한 PR에 대해서는 **`Emergency`** 라벨을 태그하고, 머지가 될 수 없는 PR에 대해서는 **`DoNotMerge`** 라벨을 태그한다.
- PR은 이슈 구현 사항을 **모두 구현한 이후**에 open할 수 있다.

## Reference
[우아한기술블로그-코드 리뷰 문화 개선 이야기](https://techblog.woowahan.com/7152/)
