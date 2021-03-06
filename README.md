# 字符集分析过滤工具 CharsetFilter 
文本字符集处理工具

##概要说明 

UTF-8字符集分析过滤工具 CharsetFilter

版本: V 1.0.3

更新：2020/6/8 13:59

工具说明：本工具把UTF8字符集分成了40个子集，可对文本文件中的字符集进行分析，
统计各类字符的总数以及出现的种类数。同时还可以方便地过滤或者保留的字符，
特别适合NLP等领域中对不可见字符的过滤分析等处理。

博客： https://blog.csdn.net/xmxoxo/article/details/102544975

## 安装与测试

直接使用pip安装
```
pip install CharsetFilter
```

测试：
```
CharsetFilter_test
```

##　对象调用使用案例

```
# 测试 
from CharsetFilter.CharsetFilter import CharsetFilter
def test ():
    objC = CharsetFilter()
    txt = '中大1三K┫□＼，≯ó㈥l｡ ･ ･ ｡ ﾉ ♡不ε﹣￥▽￣ˊˋ﹉▲āōē﹑'
    
    strRet = objC.charAnalyze (txt, detail=1)
    print('字符集分析报告'.center(40,'-'))
    print(strRet)
    
    remove = []
    remain = [2, 36] # 只保留 中文汉字 和 英文半角
    rettxt = objC.txtfilter(txt, remove=remove, remain=remain)
    print('过滤结果：\n%s' % rettxt)
    print('原始长度:%d, 过滤后长度:%d' % ( len(txt), len(rettxt)))
```


## 命令行使用案例


分析文本字符集，输出简要信息
```
CharsetFilter --file ./111.txt 
```

分析文本字符集，输出详细信息
```
CharsetFilter --file ./111.txt --detail 1
```

分析文本字符集，按默认值过滤(过滤 "其它字符 0"和 "控制字符 3")，并保存过滤结果(自动命名)
```
CharsetFilter --file ./111.txt --filter 1
```


分析文本字符集，仅保留 1,2,36,39，并保存过滤结果(自动命名)
```
CharsetFilter --file ./111.txt --filter 1 --remain_charset 1 2 36 39

```

## 字符集清单如下
```
'其它字符',  #0 除以下标识的范围之外的字符，基本可认为是不可显示字符
'系统字符',  #1 仅含三个：换行，制表，回车
'英文半角',  #2 包含数字，字母，符号，空格
'控制字符',  #3 非显示字符；
'扩展半角',  #4 一些半角符号
'韩文字符',  #5
'傣文字符',  #6
'新傣文字',  #7
'标点字符',  #8
'上标下标',  #9
'字母符号',  #10
'数字符号',  #11 
'箭头字符',  #12
'数学符号',  #13 全角数学符号
'工程符号',  #14
'控制图符',  #15
'识别符号',  #16
'序号字符',  #17 带圆圈的序号字符
'制表字符',  #18
'方块元素',  #19
'杂项符号',  #20
'装饰符号',  #21
'盲文符号',  #22 
'补充符号',  #23
'部首补充',  #24
'康熙部首',  #25
'汉字结构',  #26
'标点符号',  #27
'日文字符',  #28
'韩文字母',  #29
'笔划字符',  #30
'日文拼音',  #31
'带框月份',  #32
'日期单位',  #33
'扩展汉字',  #34
'易经字符',  #35 
'基础汉字',  #36 基本汉字
'彝文字符',  #37
'韩文字符',  #38
'全角字符',  #39 全角的标点符号
```
