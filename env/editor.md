---
icon: flutter
---

# Flutter

* install fvm

```
dart pub global activate fvm
```

* Env

{% stepper %}
{% step %}
### download flutter sdk


{% endstep %}

{% step %}
### install fvm

```
dart pub global activate fvm
```
{% endstep %}

{% step %}
FVM\_HOME

D:\programtools\fvm
{% endstep %}

{% step %}
FLUTTER\_STORAGE\_BASE\_URL

```
https://storage.flutter-io.cn
```
{% endstep %}

{% step %}
PUB\_CACHE

```
D:\ProgramTools\PUB_CACHE //和项目在同一个盘符
```
{% endstep %}

{% step %}
PUB\_HOSTED\_URL

```
https://pub.flutter-io.cn
```
{% endstep %}

{% step %}
PATH

```
D:\programtools\fvm\default\bin
```
{% endstep %}
{% endstepper %}

* Note

注： 安装flutter sdk 时 github 访问不到

1. 清除代理

```
git config --global --unset http.proxy
git config --global --unset https.proxy
```

2. 设置代理

```
git config --global http.proxy http://127.0.0.1:7890
```

3. 查看是否生效

```
git config --global -l
```

