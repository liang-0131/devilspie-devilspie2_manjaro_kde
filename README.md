# devilspie2_manjaro_kde
## 在manjaro kde下直接安装编译好的包即可
devilspie2和devilspie区别：2无模糊功能
#### 编译于2021年10月02日

### manjoaro or arch
1. 安装devilspie   
```
sudo pacman -S devilspie
```

2. 创建文件夹与配置文件 
```
mkdir -p ~/.devilspie  
nvim ~/.devilspie/obsidian.ds
```

3. 在终端中获取“obsidian"窗口CLASS值（可忽略）
```
xprop | grep 'CLASS'
```

4. 在刚创建的`.ds` 文件中写入：
```

(
if (contains (window_class) "obsidian")
    (begin
        (spawn_async (str "xprop -id " (window_xid) " -f _KDE_NET_WM_BLUR_BEHIND_REGION 32c -set _KDE_NET_WM_BLUR_BEHIND_REGION 0 "))
        (spawn_async (str "xprop -id " (window_xid) " -f _NET_WM_WINDOW_OPACITY 32c -set _NET_WM_WINDOW_OPACITY 0xCC000000"))
    )
)

```

5. 透明度的计算方式，对于上面的`0xcc000000`
```
85%=85/100*255=216.76
216.76 十进制=D8.C 十六进制=0xD8000000
```
6. 生效在终端下输入

```
devilspie
```
7. 可添加至开机自动启动
