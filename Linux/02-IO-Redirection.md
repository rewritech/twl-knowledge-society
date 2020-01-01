## IO redirection
> Input Output 방향을 바꾼다.

1. #### output: 출력
    > 출력을 방향을 파일로 돌린다.
    * '>': redirection 의미로 출력방향을 파일 등으로 설정
    * '1>': 위의 >와 같은 스탠다드 의미로 1은 생략되어있음
    * '2>': 스탠다드가 아닌 에러 아웃풋을 의미

    ```bash
    # 리스트 확인
    [ec2-user@ip-172-31-43-73 ~]$ ls -l
    total 16
    -rw-rw-r-- 1 ec2-user ec2-user  132 Dec 15 07:49 hello.html
    -rw-rw-r-- 1 ec2-user ec2-user   63 Dec 28 06:36 linux.txt
    drwxrwxr-x 9 ec2-user ec2-user 4096 Dec 21 07:29 react
    drwxrwxr-x 3 ec2-user ec2-user 4096 Dec 21 07:54 tes

    # 리스트 입력파일 생성
    [ec2-user@ip-172-31-43-73 ~]$ ls -l > result.txt
    [ec2-user@ip-172-31-43-73 ~]$ ls -l
    total 20
    -rw-rw-r-- 1 ec2-user ec2-user  132 Dec 15 07:49 hello.html
    -rw-rw-r-- 1 ec2-user ec2-user   63 Dec 28 06:36 linux.txt
    drwxrwxr-x 9 ec2-user ec2-user 4096 Dec 21 07:29 react
    -rw-rw-r-- 1 ec2-user ec2-user  296 Jan  1 15:03 result.txt
    drwxrwxr-x 3 ec2-user ec2-user 4096 Dec 21 07:54 tes

    # 확인 cat
    [ec2-user@ip-172-31-43-73 ~]$ cat result.txt
    total 16
    -rw-rw-r-- 1 ec2-user ec2-user  132 Dec 15 07:49 hello.html
    -rw-rw-r-- 1 ec2-user ec2-user   63 Dec 28 06:36 linux.txt
    drwxrwxr-x 9 ec2-user ec2-user 4096 Dec 21 07:29 react
    -rw-rw-r-- 1 ec2-user ec2-user    0 Jan  1 15:03 result.txt
    drwxrwxr-x 3 ec2-user ec2-user 4096 Dec 21 07:54 tes

    # '>'로 에러 아웃풋 처리
    [ec2-user@ip-172-31-43-73 ~]$  rm nofile.txt
    rm: cannot remove ‘nofile.txt’: No such file or directory
    [ec2-user@ip-172-31-43-73 ~]$  rm nofile.txt > result.txt
    rm: cannot remove ‘nofile.txt’: No such file or directory
    [ec2-user@ip-172-31-43-73 ~]$ cat result.txt
    [ec2-user@ip-172-31-43-73 ~]$

    # '2>'로 에러 아웃풋 처리
    [ec2-user@ip-172-31-43-73 ~]$  rm nofile.txt 1> result.txt
    rm: cannot remove ‘nofile.txt’: No such file or directory
    [ec2-user@ip-172-31-43-73 ~]$  rm nofile.txt 2> error.log
    [ec2-user@ip-172-31-43-73 ~]$ cat error.log
    rm: cannot remove ‘nofile.txt’: No such file or directory

    # '1>'과 '2>'의 혼합
    [ec2-user@ip-172-31-43-73 ~]$ rm nofile.txt 1>true.txt 2> false.log
    [ec2-user@ip-172-31-43-73 ~]$ ls -l
    total 20
    -rw-rw-r-- 1 ec2-user ec2-user   62 Jan  1 15:25 false.log # 파일 사이즈 62
    -rw-rw-r-- 1 ec2-user ec2-user  132 Dec 15 07:49 hello.html
    -rw-rw-r-- 1 ec2-user ec2-user   63 Dec 28 06:36 linux.txt
    drwxrwxr-x 9 ec2-user ec2-user 4096 Dec 21 07:29 react
    drwxrwxr-x 3 ec2-user ec2-user 4096 Dec 21 07:54 tes
    -rw-rw-r-- 1 ec2-user ec2-user    0 Jan  1 15:25 true.txt # 파일 사이즈 0
    ```