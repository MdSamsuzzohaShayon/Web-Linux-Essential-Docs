| Commands | Explanation  |
|-|-|
| touch test.sh | Creating file |
| cat /etc/passwd > test.sh | Taking all text from passwd to test.sh |
| ls -lah | See all file |
| chmod u=rwx test.sh | Set read, write, execute permission to current user |
| nano test.sh | In nano white `echo "hello world"` |
| ./test.sh | It will execute the file |
| chmod go=rwx test.sh | Set the same permission for all users in the group |
| go | g for group, o for other user, a for all users |
| chmod go-rwx test.sh | Remove permission for all users in the group |
| chmod 444 test.sh | Setting permission by using binary or oqutal  |
| 444 | first for means current user, 2nd 4 group, 3rd 4 other user |
| chmod 421 test.sh | Setting reading permission for current user, write for group execute for other |
| chmod 765 test.sh | Setting rwx for current user, rw for group, rx for others user |
| 765 | 4+2+1=7 for current user, 4+2=6 for group, 4+1=5 for others user |