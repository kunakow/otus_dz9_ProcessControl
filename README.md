# Домашнее задание. Управление процессами.

## Домашнее задание
```
Работаем с процессами
Задания на выбор
1) написать свою реализацию ps ax используя анализ /proc
- Результат ДЗ - рабочий скрипт который можно запустить
2) написать свою реализацию lsof
- Результат ДЗ - рабочий скрипт который можно запустить
3) дописать обработчики сигналов в прилагаемом скрипте, оттестировать, приложить сам скрипт, инструкции по использованию
- Результат ДЗ - рабочий скрипт который можно запустить + инструкция по использованию и лог консоли
4) реализовать 2 конкурирующих процесса по IO. пробовать запустить с разными ionice
- Результат ДЗ - скрипт запускающий 2 процесса с разными ionice, замеряющий время выполнения и лог консоли
5) реализовать 2 конкурирующих процесса по CPU. пробовать запустить с разными nice
- Результат ДЗ - скрипт запускающий 2 процесса с разными nice и замеряющий время выполнения и лог консоли
```

#### Написать свою реализацию ps ax используя анализ /proc:

[psax.sh:](https://github.com/kunakow/otus_dz9_ProcessControl/blob/main/psax.sh)
```
[root@localhost vagrant]# sh psax.sh
PID                           USER                          COMM                                                                                 STAT      RSS
1                             root                          /usr/lib/systemd/systemd--switched-root--system--deserialize21                       S         6720
2                             root                          [kthreadd]                                                                           S
4                             root                          [kworker/0:0H]                                                                       S
5                             root                          [kworker/u2:0]                                                                       S
6                             root                          [ksoftirqd/0]                                                                        S
7                             root                          [migration/0]                                                                        S
8                             root                          [rcu_bh]                                                                             S
9                             root                          [rcu_sched]                                                                          R
10                            root                          [lru-add-drain]                                                                      S
11                            root                          [watchdog/0]                                                                         S
13                            root                          [kdevtmpfs]                                                                          S
14                            root                          [netns]                                                                              S
15                            root                          [khungtaskd]                                                                         S
16                            root                          [writeback]                                                                          S
17                            root                          [kintegrityd]                                                                        S
18                            root                          [bioset]                                                                             S
19                            root                          [bioset]                                                                             S
20                            root                          [bioset]                                                                             S
21                            root                          [kblockd]                                                                            S
22                            root                          [md]                                                                                 S
23                            root                          [edac-poller]                                                                        S
24                            root                          [watchdogd]                                                                          S
25                            root                          [kworker/0:1]                                                                        S
26                            root                          [kworker/u2:1]                                                                       S
33                            root                          [kswapd0]                                                                            S
34                            root                          [ksmd]                                                                               S
35                            root                          [crypto]                                                                             S
43                            root                          [kthrotld]                                                                           S
44                            root                          [kmpath_rdacd]                                                                       S
45                            root                          [kaluad]                                                                             S
46                            root                          [kpsmoused]                                                                          S
47                            root                          [ipv6_addrconf]                                                                      S
61                            root                          [deferwq]                                                                            S
96                            root                          [kauditd]                                                                            S
```

#### Написать свою реализацию lsof

[lsof.sh:](https://github.com/kunakow/otus_dz9_ProcessControl/blob/main/lsof.sh)
```
[root@localhost vagrant]# sh lsof.sh
PID        USER                 NAME                                      COMM
1          root                 /usr/lib/systemd/systemd               systemd
1          root                 /usr/lib/systemd/systemd               systemd
1          root                 /usr/lib/systemd/systemd               systemd
1          root                 /usr/lib64/libuuid.so.1.3.0            systemd
1          root                 /usr/lib64/libuuid.so.1.3.0            systemd
1          root                 /usr/lib64/libuuid.so.1.3.0            systemd
1          root                 /usr/lib64/libuuid.so.1.3.0            systemd
1          root                 /usr/lib64/libblkid.so.1.1.0           systemd
1          root                 /usr/lib64/libblkid.so.1.1.0           systemd
1          root                 /usr/lib64/libblkid.so.1.1.0           systemd
1          root                 /usr/lib64/libblkid.so.1.1.0           systemd
1          root                 /usr/lib64/libz.so.1.2.7               systemd
1          root                 /usr/lib64/libz.so.1.2.7               systemd
1          root                 /usr/lib64/libz.so.1.2.7               systemd
1          root                 /usr/lib64/libz.so.1.2.7               systemd
1          root                 /usr/lib64/liblzma.so.5.2.2            systemd
1          root                 /usr/lib64/liblzma.so.5.2.2            systemd
1          root                 /usr/lib64/liblzma.so.5.2.2            systemd
1          root                 /usr/lib64/liblzma.so.5.2.2            systemd
1          root                 /usr/lib64/libcap-ng.so.0.0.0          systemd
1          root                 /usr/lib64/libcap-ng.so.0.0.0          systemd
1          root                 /usr/lib64/libcap-ng.so.0.0.0          systemd
1          root                 /usr/lib64/libcap-ng.so.0.0.0          systemd
1          root                 /usr/lib64/libattr.so.1.1.0            systemd
1          root                 /usr/lib64/libattr.so.1.1.0            systemd
1          root                 /usr/lib64/libattr.so.1.1.0            systemd
1          root                 /usr/lib64/libattr.so.1.1.0            systemd
1          root                 /usr/lib64/libdl-2.17.so               systemd
1          root                 /usr/lib64/libdl-2.17.so               systemd
1          root                 /usr/lib64/libdl-2.17.so               systemd
1          root                 /usr/lib64/libdl-2.17.so               systemd
1          root                 /usr/lib64/libpcre.so.1.2.0            systemd
1          root                 /usr/lib64/libpcre.so.1.2.0            systemd
1          root                 /usr/lib64/libpcre.so.1.2.0            systemd
1          root                 /usr/lib64/libpcre.so.1.2.0            systemd
1          root                 /usr/lib64/libc-2.17.so                systemd
1          root                 /usr/lib64/libc-2.17.so                systemd
1          root                 /usr/lib64/libc-2.17.so                systemd
1          root                 /usr/lib64/libc-2.17.so                systemd
1          root                 /usr/lib64/libpthread-2.17.so          systemd
1          root                 /usr/lib64/libpthread-2.17.so          systemd
1          root                 /usr/lib64/libpthread-2.17.so          systemd
1          root                 /usr/lib64/libpthread-2.17.so          systemd
1          root                 /usr/lib64/libgcc_s-4.8.5-20150702.so.1         systemd
1          root                 /usr/lib64/libgcc_s-4.8.5-20150702.so.1         systemd
1          root                 /usr/lib64/libgcc_s-4.8.5-20150702.so.1         systemd
1          root                 /usr/lib64/libgcc_s-4.8.5-20150702.so.1         systemd
1          root                 /usr/lib64/librt-2.17.so               systemd
1          root                 /usr/lib64/librt-2.17.so               systemd
1          root                 /usr/lib64/librt-2.17.so               systemd
1          root                 /usr/lib64/librt-2.17.so               systemd
1          root                 /usr/lib64/libmount.so.1.1.0           systemd
1          root                 /usr/lib64/libmount.so.1.1.0           systemd
1          root                 /usr/lib64/libmount.so.1.1.0           systemd
1          root                 /usr/lib64/libmount.so.1.1.0           systemd
1          root                 /usr/lib64/libkmod.so.2.2.10           systemd
1          root                 /usr/lib64/libkmod.so.2.2.10           systemd
1          root                 /usr/lib64/libkmod.so.2.2.10           systemd
1          root                 /usr/lib64/libkmod.so.2.2.10           systemd
1          root                 /usr/lib64/libaudit.so.1.0.0           systemd
1          root                 /usr/lib64/libaudit.so.1.0.0           systemd
1          root                 /usr/lib64/libaudit.so.1.0.0           systemd
1          root                 /usr/lib64/libaudit.so.1.0.0           systemd
1          root                 /usr/lib64/libpam.so.0.83.1            systemd
1          root                 /usr/lib64/libpam.so.0.83.1            systemd
1          root                 /usr/lib64/libpam.so.0.83.1            systemd
1          root                 /usr/lib64/libpam.so.0.83.1            systemd
1          root                 /usr/lib64/libcap.so.2.22              systemd
1          root                 /usr/lib64/libcap.so.2.22              systemd
1          root                 /usr/lib64/libcap.so.2.22              systemd
1          root                 /usr/lib64/libcap.so.2.22              systemd
1          root                 /usr/lib64/libselinux.so.1             systemd
1          root                 /usr/lib64/libselinux.so.1             systemd
1          root                 /usr/lib64/libselinux.so.1             systemd
1          root                 /usr/lib64/libselinux.so.1             systemd
1          root                 /usr/lib64/ld-2.17.so                  systemd
1          root                 /etc/selinux/targeted/contexts/files/file_contexts.homedirs.bin         systemd
1          root                 /etc/selinux/targeted/contexts/files/file_contexts.bin         systemd
1          root                 /usr/lib64/ld-2.17.so                  systemd
1          root                 /usr/lib64/ld-2.17.so                  systemd
1          root                 /                                      systemd
2          root                 /                                     kthreadd
4          root                 /                                 kworker/0:0H
5          root                 /                                 kworker/u2:0
6          root                 /                                  ksoftirqd/0
7          root                 /                                  migration/0
8          root                 /                                       rcu_bh
9          root                 /                                    rcu_sched
10         root                 /                                lru-add-drain
11         root                 /                                   watchdog/0
13         root                 /                                    kdevtmpfs
14         root                 /                                        netns
15         root                 /                                   khungtaskd
16         root                 /                                    writeback
17         root                 /                                  kintegrityd
18         root                 /                                       bioset
19         root                 /                                       bioset
20         root                 /                                       bioset
21         root                 /                                      kblockd
22         root                 /                                           md
23         root                 /                                  edac-poller
24         root                 /                                    watchdogd
26         root                 /                                 kworker/u2:1
33         root                 /                                      kswapd0
34         root                 /                                         ksmd
35         root                 /                                       crypto
43         root                 /                                     kthrotld
44         root                 /                                 kmpath_rdacd
45         root                 /                                       kaluad
46         root                 /                                    kpsmoused
47         root                 /                                ipv6_addrconf
61         root                 /                                      deferwq
96         root                 /                                      kauditd

```

