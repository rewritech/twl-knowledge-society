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

1. ### pipeline
    > 하나의 명령의 실행 결과를 다른 곳의 입력으로 줌
    * grep: 필요한 정보가 포함된 행을 찾음
    * pipe: | 정보 연결
    ```bash
    # grep: 정보 검색
    # 파일 내 정보
    [ec2-user@ip-172-31-43-73 ~]$ nano linux.txtKV
    [ec2-user@ip-172-31-43-73 ~]$ cat linux.txt
    1abcdefg
    a2bcdefg
    abc3defg
    abcd4efg
    abcde5fg
    abcdef6g
    abcdefg7
    [ec2-user@ip-172-31-43-73 ~]$ grep 3 linux.txt
    abc3defg

    # pipe: | 명령어 정보 내에서 검색
    [ec2-user@ip-172-31-43-73 ~]$ ls --help | grep sort
    Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.
    -c                         with -lt: sort by, and show, ctime (time of last
                                with -l: show ctime and sort by name;
                                otherwise: sort by ctime, newest first
    -f                         do not sort, enable -aU, disable -ls --color
                                can be augmented with a --sort option, but any
                                use of --sort=none (-U) disables grouping
    -r, --reverse              reverse order while sorting
    -S                         sort by file size
        --sort=WORD            sort by WORD instead of name: none (-U), size (-S),
                                as sort key if --sort=time
    -t                         sort by modification time, newest first
    -u                         with -lt: sort by, and show, access time;
                                with -l: show access time and sort by name;
                                otherwise: sort by access time
    -U                         do not sort; list entries in directory order
    -v                         natural sort of (version) numbers within text
    -X                         sort alphabetically by entry extension

    # 복수 pipe: and 검색
    [ec2-user@ip-172-31-43-73 ~]$ ls --help | grep sort | grep file
    -S                         sort by file size

    # ps aux: 현재 실행중인 프로그램에서 pipe grep 이용 검색
    [ec2-user@ip-172-31-43-73 ~]$ ps aux | grep amazon
    root      2264  0.0  1.3 291844 13404 ?        Ssl  Nov30   0:15 /usr/bin/amazon-ssm-agent
    ec2-user  9188  0.0  0.2 110520  2112 pts/0    S+   06:46   0:00 grep --color=auto amazon
    ```