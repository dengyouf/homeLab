- create dir for gitlab

```
mkdir /data/application/gitlab/{data,logs,config} -pv 
cd /data/application/gitlab/ && docker-compose up 
```

- modify gitlab root password

```

gitlab]# docker-compose  exec  gitlab bash
root@gtlab:/# gitlab-rails console -e production
--------------------------------------------------------------------------------
 Ruby:         ruby 2.7.5p203 (2021-11-24 revision f69aeb8314) [x86_64-linux]
 GitLab:       15.1.5 (0ab7bf7ee38) FOSS
 GitLab Shell: 14.7.4
 PostgreSQL:   13.6
------------------------------------------------------------[ booted in 50.65s ]
Loading production environment (Rails 6.1.4.7)
=> #<User id:1 @root>
=> "gitlab123"
=> "gitlab123"
=> true
root@gtlab:/# exit
exit
[root@gitlab gitlab]# 
```
