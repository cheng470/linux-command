nova, OpenStack Nova command line client

# 例子

```sh
# 查看所有 server
nova list

# 查看所有 flavor
nova flavor-list

# 查看 server 信息
nova show 9137462f-f1b1-40da-bd0b-75c168d88106 --minimal --wrap 120

# 查看 request 信息
nova instance-action node-1 req-954e0c73-490a-4b03-8256-1ef9701a7a3a
```