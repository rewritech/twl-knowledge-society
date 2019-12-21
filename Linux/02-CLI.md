## why using CLI?
> CLI를 사용하는 이유
1. #### GUI vs CLI
    > CLI방식이 GUI방식에 비해 컴퓨터 에너지를 훨씬 적게 사용
    * 일반 사용자는 GUI방식으로 그래픽 방식 사용
    * 서버 등 무거운 작업은 CLI로 처리가 가볍게 사용
    * GUI방식은 쉽지만, 업무에 필요한 조작절차 및 대기시간이 많음
    * CLI방식은 명령어로 업무결과까지 자동으로 받을 수 있음

1. #### sequence execution(semicolon)
    > CLI의 장점을 느끼면 성공
    * 순차적으로 실행하는 명령어를 한번에 도입할 수 있다.
    * 장시간 작업 명령어의 종료대기 필요 없이, 다음 명령어 자동실행가능
    ```bash
    # 명령어 하나씩 순서대로 입력
    [ec2-user@ip-172-31-43-73 tes]$ mkdir why
    [ec2-user@ip-172-31-43-73 tes]$ cd why
    [ec2-user@ip-172-31-43-73 why]$ pwd
    /home/ec2-user/tes/why

    # 명령어 여러개를 한번에 입력
    [ec2-user@ip-172-31-43-73 tes]$ mkdir why;cd why; pwd
    /home/ec2-user/tes/why
    ```