# 一、集成在idea中的相关问题

1. 将文件上传至github中时问题：OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443

   解决：在项目根目录打开git命令行，输入：git config --global --unset http.proxy

   ​