# Install Anaconda On Centos

1. 下载Anaconda安装脚本
    
    ```bash
    $ cd /tmp
    $ curl -O https://repo.anaconda.com/archive/Anaconda3-5.3.1-Linux-x86_64.sh
    ```
2. 验证安装包的完整性

    * 使用`sha256sum`命令验证安装包脚本：
        
        ```bash
        $ sha256sum Anaconda3-5.3.1-Linux-x86_64.sh
        ```
    * 执行后，你将会看到以下界面信息

        ``` Output
        $ d4c4256a8f46173b675dd6a62d12f566ed3487f932bab6bb7058f06c124bcc27  Anaconda3-5.3.1-Linux-x86_64.sh
        ```
3. 执行Anaconda安装脚本

    * 执行脚本
 
        ``` bash
        $ bash Anaconda3-5.3.1-Linux-x86_64.sh
        ```
    * 执行后，你将会看到以下界面信息

        ```Output
        Welcome to Anaconda3 5.3.1
        
        In order to continue the installation process, please review the license
agreement.
        Please, press ENTER to continue
        ```
    * 输入`ENTER`阅读浏览相关条款
    
        ``` OutPut
        Do you accept the license terms? [yes|no]
        ```
    * 输入`yes`同意条款
    
        ```Output
        Anaconda3 will now be installed into this location:
/root/anaconda3

        - Press ENTER to confirm the location
        - Press CTRL-C to abort the installation
        - Or specify a different location below
        ```
        
    * 默认Anaconda会安装在用户目录下，按`ENTER`确认安装或者退出安装
    
        再次过程中，其安装包需要依赖`bzip2`，若为安装则会输出一下界面：
    
        ``` Output 
        If you get an error saying bunzip2: command not found, install the bzip2 package with:
sudo yum install bzip2.
        ```
        接下来根据提示安装`bzip2`，并且删除之前安装的文件即安装目录下的`Anaconda`,`rm -rf ./Anaconda`,之后重新执行安装脚本。
        
        * 重新安装后，界面将提示：

            ```bash
            Do you wish the installer to initialize Anaconda3
in your /root/.bashrc ? [yes|no]
[no] >>> yes
            ```
            需要选择是否更新环境变量，
5. 验证安装是否成功

# Uninstalling Anaconda

1. 移除Anaconda安装目录

    ```bash
    $ rm -rf ~/anaconda3
    ```

2. 移除系统环境变量
编辑`~/.bashrc`文件，移除Anaconda初始化

    ``` ~/.bashrc
    # added by Anaconda3 5.3.1 installer
    # >>> conda init >>>
    # !! Contents within this block are managed by 'conda init' !!
    __conda_setup="$(CONDA_REPORT_ERRORS=false '/home/linuxize/anaconda3/bin/conda' shell.bash hook 2> /dev/null)"
    if [ $? -eq 0 ]; then
        \eval "$__conda_setup"
    else
        if [ -f "/home/linuxize/anaconda3/etc/profile.d/conda.sh" ]; then
            . "/home/linuxize/anaconda3/etc/profile.d/conda.sh"
            CONDA_CHANGEPS1=false conda activate base
        else
            \export PATH="/home/linuxize/anaconda3/bin:$PATH"
        fi
    fi
    unset __conda_setup
    # <<< conda init <<<
    ```
4. 移除系统中关于Anaconda相关的隐藏文件

    ```bash
    $ rm -rf ~/.condarc ~/.conda ~/.continuum
    ```