# google

---


我们先来看看Google的部分语法：

intitle：搜索网页标题中包含有特定字符的网页。例如输入“intitle: cbi”，这样网页标题中带有cbi的网页都会被搜索出来。

inurl：搜索包含有特定字符的URL。例如输入“inurl:cbi”，则可以找到带有cbi字符的URL。

intext:搜索网页正文内容中的指定字符，例如输入“intext:cbi”。这个语法类似我们平时在某些网站中使用的“文章内容搜索”功能。

Filetype:搜索指定类型的文件。例如输入“filetype:cbi”，将返回所有以cbi结尾的文件URL。

Site：找到与指定网站有联系的URL。例如输入“Site：family.chinaok.com”。所有和这个网站有联系的URL都会被显示。

这些就是Google的常用语法，也是Google Hack的必用语法。虽然这只是Google语法中很小的部分，但是合理使用这些语法将产生意想不到的效果。

了解了Google的基本语法后，我们来看一下黑客是如何使用这些语法进行Google Hack的，这些语法在入侵的过程中又会起到怎样的作用呢？

1.寻找网站的后台登录页面

Intitle

intitle语法通常被用来搜索网站的后台、特殊页面和文件，通过在Google中搜索“intitle:登录”、“intitle:管理”就可以找到很多网站的后台登录页面。此外，intitle语法还可以被用在搜索文件上，例如搜索“intitle:"indexof"etc/shadow”就可以找到Linux中因为配置不合理而泄露出来的用户密码文件。

Inurl

Google Hack中，inurl发挥的作用的最大，主要可以分为以下两个方面:寻找网站后台登录地址，搜索特殊URL。

寻找网站后台登录地址：和intitle不同的是，inurl可以指定URL中的关键字，我们都知道网站的后台URL都是类似login.asp、admin.asp为结尾的，那么我们只要以“inurl:login.asp”、“inurl:admin.asp”为关键字进行搜索，同样可以找到很多网站的后台。此外，我们还可以搜索一下网站的数据库地址，以“inurl:data”、“inurl:db”为关键字进行搜索即可。

搜索特殊URL：通过inurl语法搜索特殊URL，我们可以找到很多网站程序的漏洞，例如最早IIS中的Uncode目录遍历漏洞，我们可以构造“inurl:／winnt／system32／cmd exe?／c+dir”这样的关键字进行搜索，不过目前要搜索到存在这种古董漏洞的网站是比较困难的。再比如前段日子很火的上传漏洞，我们使用““inurl:upload.asp”或“inurl:upload_soft.asp”即可找到很多上传页面，此时再用工具进行木马上传就可以完成入侵。

Intext
intext的作用是搜索网页中的指定字符，这貌似在Google Hack中没有什么作用，不过在以“intext:to parent directory”为关键字进行搜索后，我们会很惊奇的发现，无数网站的目录暴露在我们眼前。我们可以在其中随意切换目录，浏览文件，就像拥有了一个简单的Webshell。形成这种现象的原因是由于IIS的配置疏忽。同样，中文IIS配置疏忽也可能出现类似的漏洞，我们用“intext:转到父目录”就可以找到很多有漏洞的中文网站。

2.随意浏览网站中的文件

Filetype

Filetype的作用是搜索指定文件。假如我们要搜索网站的数据库文件，那么可以以“filetype:mdb”为关键字进行搜索，很快就可以下载到不少网站的数据库文件。当然，Filetype语法的作用不仅于此，在和其他语法配合使用的时候更能显示出其强大作用。

Site

黑客使用Site，通常都是做入侵前的信息收集。“Site:target.com”来获取相关网页，从中提取有用的资料。Site语法可以显示所有和目标网站有联系的页面，从中或多或少存在一些关于目标网站的资料，这对于黑客而言就是入侵的突破口，是关于目标网站的一份详尽的报告。

语法组合，威力加倍

虽然上文中介绍的这几个语法能各自完成入侵中的一些步骤，但是只使用一个语法进行入侵，其效率是很低下的。Google Hack的威力在于能将多个语法组合起来，这样就可以快速地找到我们需要的东西。下面我们来模拟黑客是如何使用Google语法组合来入侵一个网站的。

3.搜索相关页面

下载网站的数据库

搜索“Site:target.com Filetype:mdb”就可以寻找目标网站的数据库，其中的Site语法限定搜索范围，Filetype决定搜索目标。用这种方法有一个缺点，就是下载到数据库的成功率较低。在这里我们还可以采用另一种语法组合，前提是目标网站存在IIS配置缺陷，即可以随意浏览站点文件夹，我们搜索“Site:target.com intext:to parent directory”来确定其是否存在此漏洞。在确定漏洞存在后，可以使用“Site:target.com intext:to parent directory+intext.mdb”进行数据库的搜索。

4.找到网站数据库

登录后台管理

下载到数据库后，我们就可以从中找到网站的管理员帐户和密码，并登录网站的后台。对于网站后台的查找，可以使用语法组合“Site:target.com intitle:管理”或者“Site:target.com inurl:login.asp”进行搜索，当然我们可以在这里进行联想，以不同的字符进行搜索，这样就有很大的概率可以找到网站的后台管理地址。接下去黑客就可以在后台上传Webshell，进一步提升权限，在此不再阐述。

5.利用其他漏洞

如果下载数据库不成功，我们还可以尝试其他的入侵方法。例如寻找上传漏洞，搜索 “Site:target.com inurl:upload.asp”。此外，我们还可以根据一些程序漏洞的特征，定制出Google Hack的语句。
