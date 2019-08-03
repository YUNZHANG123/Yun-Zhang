1. geting data of all friends in Wechat, and saving it to a document.
2. coding to read the document and make a pie graph to demonstrate the sex ratio of the friends.

code:

#!/usr/bin/env python3
# -*- coding: utf-8 -*-
import webbrowser
from pyecharts import Pie
sex = []
with open('friends_data.txt', mode='r', encoding='utf-8') as f:
    rows = f.readlines()
    for row in rows:
        sex.append(row.split(',')[2])

attr = ['帅哥', '美女', '未知']
value = [sex.count('1'), sex.count('2'), sex.count('0')]

pie = Pie('好友性别比例', '好友总人数：%d' % len(sex), title_pos='center')
pie.add('', attr, value, radius=[30, 75], rosetype='area', is_label_show=True,
        is_legend_show=True, legend_top='bottom')

pie.render('sex_ratio.html')

webbrowser.open('sex_ratio.html', new=2)
