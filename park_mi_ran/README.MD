## git reset vs git revert 명령어 비교하기

- reset과 revert
** 파일을 삭제했거나 제대로 벼합이 안됐을 때 이전버전으로 돌아가야할 때 사용하는 깃 명령어
<차이점은 -로 표시>
reset
    : 특정 커밋으로 되돌아갈 수 있다. 되돌린 버전 이후의 버전들은 히스토리에서 삭제된다.
    - commit 이력이 사라진다.
    - remote repository까지 컨트롤 할 수 없다. push 할 수 없다.

revert 
    : reset처럼 특정 버전으로 되돌아갈 수 있지만, 되돌린 버전 이후의 버전들의 이력은 남아있다.
    - commit 이력이 그대로 유지된다. 
    - 원격 저장소에 push를 한 상태에서 되돌릴 수 있다.( revert명령어가 먼 과거의 버전으로 돌아갈 수 있다.)
<명령어 정리>
1. get checkout

    - get checkout . : working directory 에서 수정한 모든 파일 (git add이전)을 현재 버전으로 되돌리기
    - get checkout --{file} : woring directory에서 수정한 파일(git add이전)을 현재 버전으로 되돌리기

2. git reset

    - git reset . : add무효화 하기(현재 버전으로 되돌리기)
    - git reset {commit번호} : 특정 버전으로 되돌리지만, 커밋 이력 삭제/ 파일 내용은 유지
    - git reset --hard{commit번호} : 파일 내용까지 되돌림
    - git reset --soft{commit번호} : 파일 내용은 그대로 유지하면서 staging area에 올림(add 상태)
    - git reset -merge ORIG_HEAD : 바로 이전 병합 취소

3. git revert

    - git revert {commit번호} : 특정 버전으로 되돌리는데 파일내용은 그대로 유지하고 버전 이후의 모든 commit이력은 그대로 보존
    - git revert --mainline 숫자 : 과거 병합을 취소 / 숫자로 명시된 브랜치 라인을 기준으로 되돌아간다.