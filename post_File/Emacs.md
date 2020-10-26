# Emacs
---

C-f 后一个字符

C-b 前一个字符

C-p 上一行

C-n 下一行

M-f 后一个单词

M-b 前一个单词

C-a 行首

C-e 行尾

C-v 向下翻一页

M-v 向上翻一页

M-< 到文件开头

M-> 到文件末尾

C-x C-f "find"文件, 即在缓冲区打开/新建一个文件

C-x C-s 保存文件

C-x C-w 使用其他文件名另存为文件

C-x C-v 关闭当前缓冲区文件并打开新文件

C-x i 在当前光标处插入文件

C-x b 新建/切换缓冲区

C-x C-b 显示缓冲区列表

C-x k 关闭当前缓冲区

C-z 挂起emacs

C-x C-c 关闭emacs

---

剪切: C-w

复制: M-w

粘贴: C-y

上一行: C-p

下一行: C-n

左移一个字符: C-b

右移一个字符: C-f

行首: C-a

行尾: C-e

文章开头: M-S-,

文章结尾: M-S-.

向上搜索: C-r

向下搜索: C-s

替换：M-S-5

撤销: C-x u

保存: C-x s

保存，不提示: C-x C-s

全选: C-x h

退出: C-x C-c

取消命令: C-g

切分成两个窗口: C-x 2

关闭其他窗口: C-x 1

切换窗口: C-x o

剪切光标到行尾: C-k

删除下一个字符: C-d

显示所有buffer：C-mouse

关闭当前buffer：C-x k

---

c+h i 

m+x global-linum-mode 显示行号

m+x emacs version

cx b //临时buffer窗口

emacs 配置文件顺序

~/.emacs

~/.emacs.d

~/.config/emcas/init.el

m+x make-directory 新建目录

m+x eshell

m+x restart-emacs

---

C-n，下一行（速记：Nextline）

C-p，前一行（速记：Previous line）

C-f，向前移动一个字符（速记：Forward）

C-b，向后退一个字符（速记：Backforward）

C-k，从光标位置到末尾删掉（速记：Kill）

C-a，回到行首（速记：a 是字母表的开始）

C-e，去往行尾（速记：End of line）

M-<，回到编辑区域最开始位置（速记：<）

M->，去往编辑区域最后的位置（速记：>）

C-v，向下翻一屏

M-v，向上翻一屏

6 自带文档

C-h t ;速记 Help Tutorial

查看快捷键的含义：

C-h k ;速记 Help Keybind

查看函数的定义以及快捷键绑定：

C-h f ;速记 Help Function

7 对外观做点改变

图形化配置M-x customize

菜单栏 menu-bar-mode

工具栏 tool-bar-mode

滚动条 scroll-bar-mode

优势：不用写 ELisp 代码

劣势：

搜索

生成的配置代码只能是单一文件配置，显得凌乱

扩展的配置不容易进行

涉及到复杂逻辑的（如条件判断）不方便配置

8 体验下用配置文件配置

创建文件 ~/.emacs 并写入一下内容：

(menu-bar-mode -1)

(tool-bar-mode -1)

(scroll-bar-mode -1)

重启 Emacs 看看实际的效果。

Emacs 配置初体验

9 认识配置文件

Emacs 配置文件的位置，会按照一下顺序去查找：

~/.emacs

~/.emacs.d

~/.config/emacs/init.el

第一个是一个单一文件配置；第二个更符合工程化；第三个仅适用于 ≥27 的版本。教程会从第一个入手，逐渐变为第二种的模式。

---

11 第一行 emacs 配置代码

已经体验了关掉菜单栏、工具栏、滚动条等。现在尝试关掉启动界面：

(setq inhibit-startup-screen t)

重启 Emacs 看看？


软件源

(setq package-archives '(

    ("melpa" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/")
    
    ("gnu" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/")
    
    ("org" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/org/")))
    
13 安装第一个 emacs 扩展

安装扩展前，需要先刷新软件源的索引。

(setq package-check-signature nil) ;个别时候会出现签名校验失败

(require 'package) ;; 初始化包管理器

(unless (bound-and-true-p package--initialized)

   (package-initialize)) ;; 刷新软件源索引
   
(unless package-archive-contents

    (package-refresh-contents))
    

unless (package-installed-p 'use-package)

   (package-refresh-contents)
   
   (package-install 'use-package))
   
14 使用 use-package 管理扩展

什么是 use-package


基本格式，并举个例子

;; 最简洁的格式

 (use-package restart-emacs)

;; 常用的格式

 (use-package smooth-scrolling
 
    :ensure t ;是否一定要确保已安装
    
    :defer nil ;是否要延迟加载
    
    :init (setq smooth-scrolling-margin 2) ;初始化参数
    
    :config (smooth-scrolling-mode t) ;基本配置参数
    
    :bind ;快捷键的绑定
    
    :hook) ;hook模式的绑定
    
建议添加的配置（部分来自 use-package 官方建议）：

(eval-and-compile

    (setq use-package-always-ensure t) ;不用每个包都手动添加:ensure t关键字
    
    (setq use-package-always-defer t) ;默认都是延迟加载，不用每个包都手动添加:defer t
    
    (setq use-package-always-demand nil)
    
    (setq use-package-expand-minimally t)
    
    (setq use-package-verbose t))
    
15 更换个主题

教程演示采用的主题是 gruvbox-theme。

(use-package gruvbox-theme

    :init (load-theme 'gruvbox-dark-soft t))
    
顺便配置一个好看一点的 Mode Line。


(use-package smart-mode-line

    :init
    
    (setq sml/no-confirm-load-theme t)
    
    (setq sml/theme 'respectful)
    
    (sml/setup))

##### 16 工程化管理配置（1）功能拆分

到此为止，在~/.emacs 中配置了很多的内容，开始显得很乱：

初始化 Elpa

安装扩展

添加主题

是时候分类处理了。就像一个开发项目那样。尝试着把配置按照功能不同拆分成不同的文件。如：

lisp/init-elpa.el用于存放 Elpa 和 Package 初始化

lisp/init-package.el用于存放安装的扩展

lisp/init-ui.el用于存放界面主题相关配置

如何在初始化文件中把它们联系在一起（调用）？

##### 17 工程化管理配置（2）文件加载与调用

先设置加载的目标目录到 load-path 中。

(add-to-list 'load-path

    (expand-file-name (concat user-emacs-directory "lisp")))
    
各个文件通过 provide 暴露对外调用的名称。如：

(provide 'init-ui)

然后在 init.el 文件中通过 require 调用：

require 'init-ui

##### 18 关于自定义的配置

建议写入一个单独的文件，对外开源的时候，该文件不被提交到 Git 中。如，custom.el

(setq custom-file

    (expand-file-name "custom.el" user-emacs-directory))
    
这样就会把通过图形界面做的一些配置，写入到这里了。

##### 19 操作系统判断

后面的部分配置会因操作系统不同而产生不同配置代码，所以有必要对操作系统进行判断。

(defconst *is-mac* (eq system-type 'darwin))

(defconst *is-linux* (eq system-type 'gnu/linux))

(defconst *is-windows* (or (eq system-type 'ms-dos) (eq system-type 'windows-nt)))

20 macOS 平台将 Command 键映射为 Meta

对于 Mac 键盘来说，Command 键距离 x 的位置与 Windows 键盘更相近，所以习惯上可以修改这个按键映射为 Meta，如果你不需

要这个设置，可以不用管。

(when *is-mac*

    (setq mac-command-modifier 'meta)
    
    (setq mac-option-modifier 'none))
    
21 通过修改字体解决 Windows 上 Emacs 的卡顿

(use-package emacs

  :if (display-graphic-p)
  
  :config
  
  ;; Font settings
  
  (if *is-windows*
  
    (progn
      (set-face-attribute 'default nil :font "Microsoft Yahei Mono 9")
      
      (dolist (charset '(kana han symbol cjk-misc bopomofo))
      
        (set-fontset-font (frame-parameter nil 'font) charset (font-spec :family "Microsoft Yahei 
        
        Mono" :size 12))))
        
  (set-face-attribute 'default nil :font "Source Code Pro for Powerline 11")))
  
22 建议增加的一点启动配置

设置系统的编码，避免各处的乱码。

(prefer-coding-system 'utf-8)

(set-default-coding-systems 'utf-8)

(set-terminal-coding-system 'utf-8)

(set-keyboard-coding-system 'utf-8)

(setq default-buffer-file-coding-system 'utf-8)

设置垃圾回收阈值，加速启动速度。

(setq gc-cons-threshold most-positive-fixnum)

23 测试启动耗时

通过 benchmark-init 包进行启动耗时的测量。

(use-package benchmark-init

  :init (benchmark-init/activate)
  
  :hook (after-init . benchmark-init/deactivate))
  
M-x benchmark-init/show-durations-tree 或者 M-x benchmark-init/show-durations-tabulated

24 中断命令输入

C-g在输入任何命令的时候，可随时通过该快捷键放弃命令的继续键入。

25 用 y/n 来代替 yes/no

(defalias 'yes-or-no-p 'y-or-n-p)

为了项目管理的统一化，可以用如下的use-package写法：

(use-package emacs :config (defalias 'yes-or-no-p 'y-or-n-p))

26 显示行号

26.1 行号的类型

从 Emacs 26 开始，自带了行号显示功能，可以通过设置display-line-numbers-type变量的值，来改变行号的类型。可取值有：

relative，相对行号

visual，可视化行号

26.2 行号配置

(use-package emacs

    :config
    
    (setq display-line-numbers-type 'relative)
    
    (global-display-line-numbers-mode t))
    
注： 有些时候我发现在 Windows 上开启了行号会让屏幕滚动的时候闪烁，此时，我们可以让其在 Windows 上不开启行号。

(use-package emacs

    :unless *is-windows*
    
    :config
    
    (setq display-line-numbers-type 'relative)
    
    (global-display-line-numbers-mode t))
    
Emacs 文本编辑

方法一，使用鼠标拖动选中

方法二，标记开始位置，然后通过移动光标到结束位置

默认使用 C-SPC 或 C-@进行开始位置的标记

对于很多场景下，C-SPC 快捷键被占用（输入法，Spotlight 等）

复制 M-w

剪切 C-w

粘贴 C-y ;; 速记 Yank

28 文本编辑之删除

场景一：从光标位置到行尾的删除 C-k

场景二：删除当前行

默认没有这样的快捷键，可以安装一个扩展来实现，crux，该扩展提供了包含该场景在内的一系列优化快捷命令。

(use-package crux

    :bind ("C-c k" . crux-smart-kill-line))
    
后面补充一节课来介绍这个扩展。

场景三：一次性删除到前/后面的第一个非空字符（删除连续的空白）

通过hungry-delete扩展实现，该功能。

(use-package hungry-delete

    :bind (("C-c DEL" . hungry-delete-backward)
    
           ("C-c d" . hungry-delete-forward)))
           
29 文本编辑之行/区域上下移动

在 VSCode 或 Jetbrains 家族的编辑器中，上下移动行/块是非常容易的，但原生的 Emacs 没有提供这样的功能。可通过插

件drag-stuff来辅助实现。

(use-package drag-stuff

  :bind (("<M-up>". drag-stuff-up)
  
         ("<M-down>" . drag-stuff-down)))
         
30 文本编辑之原生搜索/替换

Emacs 原生提供了强大的搜索和替换功能。

;; 当前位置到文档结尾的搜索

C-s

;; 当前位置到文档开始的搜索

C-r

;; 替换

M-%
替换时按下y确认替换，n跳过本处的替换，!全部替换。

31 文本编辑之强化搜索

著名的ivy-counsel-swiper三剑客，就是为了强化搜索（同时优化了一系列 Minibuffer 的操作）。

(use-package ivy

  :defer 1
  
  :demand
  
  :hook (after-init . ivy-mode)
  
  :config
  
  (ivy-mode 1)
  
  (setq ivy-use-virtual-buffers t
  
        ivy-initial-inputs-alist nil
        
        ivy-count-format "%d/%d "
        
        enable-recursive-minibuffers t
        
        ivy-re-builders-alist '((t . ivy--regex-ignore-order)))
        
  (ivy-posframe-mode 1)))

(use-package counsel

  :after (ivy)
  
  :bind (("M-x" . counsel-M-x)
  
         ("C-x C-f" . counsel-find-file)
         
         ("C-c f" . counsel-recentf)
         
         ("C-c g" . counsel-git)))

(use-package swiper

  :after ivy
  
  :bind (("C-s" . swiper)
  
         ("C-r" . swiper-isearch-backward))
         
  :config (setq swiper-action-recenter t
  
                swiper-include-line-number-in-search t))
                
32 文本编辑之自动补全

Emacs 界补全两大垄断插件，Auto-Complete和Company（Complete Anything）。时代和特性原因，Company呈现压倒性优势。

(use-package company

  :config
  
  (setq company-dabbrev-code-everywhere t
  
        company-dabbrev-code-modes t
        
        company-dabbrev-code-other-buffers 'all
        
        company-dabbrev-downcase nil
        
        company-dabbrev-ignore-case t
        
        company-dabbrev-other-buffers 'all
        
        company-require-match nil
        
        company-minimum-prefix-length 2
        
        company-show-numbers t
        
        company-tooltip-limit 20
        
        company-idle-delay 0
        
        company-echo-delay 0
        
        company-tooltip-offset-display 'scrollbar
        
        company-begin-commands '(self-insert-command))
        
  (push '(company-semantic :with company-yasnippet) company-backends)
  
  :hook ((after-init . global-company-mode)))
  
但，注意下认识到Company的不足：文档。其文档都是写在源码中的。

33 文本编辑之语法检查

默认 Emacs 自带了Flymake，但Flycheck是一个更优的方案。

建议全局启用：

(use-package flycheck

  :hook (after-init . global-flycheck-mode))
  
如果你只想在编程语言的模式下启用：

(use-package flycheck

  :hook (prog-mode . flycheck-mode))
  
34 文本编辑之行排序

M-x sort-lines

35 文本编辑之顺序更换

光标前后两个字符互换 C-t

光标前后两个单词互换 M-t

36 文本编辑之字数统计

整个 Buffer 统计

M-=

;; 或者

M-x count-words-region

选中区域统计

;; 先选中

M-x count-words

Emacs 常用插件

37 crux 优化 Emacs 常用操作

优化版的回到行首

快速打开 Emacs 配置文件

快速连接两行等

(use-package crux

  :bind (("C-a" . crux-move-beginning-of-line)
  
         ("C-c ^" . crux-top-join-line)
         
         ("C-x ," . crux-find-user-init-file)
         
         ("C-c k" . crux-smart-kill-line)))
         

如果你不喜欢用鼠标在菜单栏点击的化，你其实可以用 Which-Key 这款插件来辅助你“记忆”。

(use-package which-key

  :defer nil
  
  :config (which-key-mode))
  
当你按下一个按键时，它会提示你下一个按键的含义。并等待你去按下。

Emacs 窗口管理

39 窗口管理之 Buffer 管理

Buffer 切换

C-x b

杀死当前 Buffer

C-x k

批量管理 Buffer

C-x C-b ;; 进入Buffer列表

d ;; 标记删除

u ;; 取消当前行标记

U ;; 取消全部标记

x ;; 执行操作

? ;; 查看按键帮助

40 窗口管理之 MiniBuffer 交互优化

显示在左下角的 MiniBuffer 移动视线范围大，移动到中央位置，更合适一些。

(use-package ivy-posframe

  :init
  
  (setq ivy-posframe-display-functions-alist
  
    '((swiper . ivy-posframe-display-at-frame-center)
    
      (complete-symbol . ivy-posframe-display-at-point)
      
      (counsel-M-x . ivy-posframe-display-at-frame-center)
      
      (counsel-find-file . ivy-posframe-display-at-frame-center)
      
      (ivy-switch-buffer . ivy-posframe-display-at-frame-center)
      
      (t . ivy-posframe-display-at-frame-center)))
      
41 窗口管理之分屏

开启横向分屏 C-x 3

开启纵向分屏 C-x 2

只保留当前分屏 C-x 1

关闭当前分屏 C-x 0

42 窗口管理之分屏宽度调整

增加高度 C-x ^

增加/减少宽度 C-x { C-x }

43 窗口管理之快速切换分屏

默认可通过以下快捷键进行窗口的循环跳转： C-x o

当分屏很多的时候效率非常低。通过 ace-window 可快速进行窗口间的跳转。类似的插件较多，但该款为最佳方案。

(use-package ace-window

    :bind (("M-o" . 'ace-window)))
    
image.png

44 窗口管理之 Tab 标签页管理

C-x t 2 ;; 新建Tab

      1 ;; 关闭其它Tab
      
      0 ;; 关闭当前Tab
      
      b ;; 在新Tab中打开Buffer
      

