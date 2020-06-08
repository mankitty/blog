# Linux通过用户名获取用户的具体信息

标签（空格分隔）： Linux

---

## 实现代码
```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <pwd.h>
#include <sys/utsname.h>

int main(int argc,char *argv[])
{
    struct passwd *pwd = NULL;
    /*
     *系统文件/etc/passwd包含一个用户帐号数据库。它由行组成，每行对应一个用户，包括：
     *用户名、加密口令、用户标识符（UID）、组标识符（GID）、全名、主目录和默认shell。
     *编程接口的数据结构：
     strcut passwd {
         char *pw_name;
         char *pw_passwd;
         uid_t pw_uid;
         gid_t pw_gid;
         char *pw_gecos;
         char *pw_dir;
         char *pw_shell;
     }
    */
    
    pwd = getpwnam("cetc");
    if (pwd == NULL)
    {
        printf("user host48 is not exit.\n");
        return -1;
    }
    printf("name=%s, pass=%s, uid=%d, gid=%d, gecos=%s, dir=%s, shell=%s\n",\
                    pwd->pw_name, pwd->pw_passwd, pwd->pw_uid, pwd->pw_gid, pwd->pw_gecos, pwd->pw_dir, pwd->pw_shell);
    
    return 0;
}
```




