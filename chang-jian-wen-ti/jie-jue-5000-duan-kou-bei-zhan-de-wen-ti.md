##解决flask的端口占用

在编辑`flask`代码时，如果没有关闭`flask`的程序，默认的5000端口一直被占用。

再次运行`flask`程序时，会显示：

```py
socket.error: [Errno 48] Address already in use
```

# lsof查进程

因为之前占用的5000端口，所以直接用`lsof`查该端口占用的进程。

```py
sudo lsof -i:5000
COMMAND PID    USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
python  769 testUser    3u  IPv4 0x6ff9fe98d80592e1      0t0  TCP localhost:commplex-main (LISTEN)

```

可以看到是python占用了该端口，PID是769。可以用kill命令杀该进程，命令形式是sudo kill *pid*，其中*pid*就是pid号。

```
sudo kill 769
```