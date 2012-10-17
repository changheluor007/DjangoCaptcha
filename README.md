DjangoVerifyCode
=================
在Django中生成验证码
使用
---
####显示验证码(views.py)####
```
def code(request):
    code = Code(request)
    return code.display()
```

####检查用户输入的验证码是否正确(views.py)####
```
def index(request):
    _code = request.GET.get('code') or ''
    if not _code:
        return render('index.html',locals())

    code = Code(request)
    if code.check(_code):
        return HttpResponse('验证成功')
    else:
        return HttpResponse('验证失败')
```

依赖
----
+ PIL
+ Django >= 1.3

demo
----

+ <http://djangoverifycode.t-y.me>