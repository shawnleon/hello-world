# -*- coding: utf-8 -*-

# Get all of names and urls of company registered in butian.360.cn
# 这个程序是为了获取在360补天已经注册的所有厂商
# The code was written by Leon  *由李昂练习所写的代码
# Comply with PEP 8 rule * 遵守 PEP 8 规则

import requests

# Get the pages of company in the list of registration  *获取厂商注册列表的页数
url = "https://butian.360.cn/company/lists/page/1"
# 请求url
r = requests.get(url)
# print r.text      # 测试打印url看是否成功获取到
# Get the format of coding  *获取编码格式
r.encoding = r.apparent_encoding
html = r.content
split_page = html.split('">末页')[0]       # Split whit ">  *以">末页 分割
page = int(split_page[split_page.rfind('/') + 1:])      # 得到总页数的数字
# print split_page      # 检查分割是否成功
# print type(page)      # 查看page的类型以便和下面的%d类型相对应
print u'厂商数量共%d：' % page        # print the total amount of the name of company

# Get all names and urls of company  * 循环获取厂商的名字和url*
for i in xrange(1, page + 1):
    url = "https://butian.360.cn/company/lists/page/%d" % i
    r = requests.get(url)
    print url
    r.encoding = r.apparent_encoding
    html = r.content
    # 分割
    split_company = html.split('height="30" style="padding-left:20px;">')[1:]

    # 分割之后循环得到想要的公司name和url
    for i in split_company:
        company_name = i.split(">")[1][:-3]
        url = i.split(">")[4][:-4].ljust(30)
        print url, company_name
        # Open a file whit appending *追加写入的方式打开一个文件
        f = open('D:\\Python27\\1.txt', 'a+')
        # Write names and urls into the file *写入公司名和url
        f.write(url + company_name + '\n')
        # Close the opened file *关闭一个文件
        f.close()
