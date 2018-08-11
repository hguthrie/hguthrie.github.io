# Build DevDocs in Windows

Download software:

-  [Git for Windows](https://gitforwindows.org)
-  [Chocolatey](https://chocolatey.org/install)

## Install Git for Windows

Use Git for Windows to prevent interference with existing Windows environment and to have Git launch commands available on the shortcut menu.

Open the Git Setup file downloaded from the Git for Windows site and use the following settings during installation:

-  select **Use Git from Git Bash only**
-  select **Checkout as-is, commit Unix-style line endings**
-  select your preferred editor (can use Nano, Notepad++, or VIM)
-  select **Enable symbolic links**

### Set up SSH key

1.  Open Git Bash.

1.  Create a working directory for Git repositories and change to the new directory.

    ```bash
    mkdir <directory-name>
    ```

1.  Follow the [Generating a new SSH](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) instructions.

## Install Chocolatey
Only Administrators can use Chocolatey features.

1.  Open the command prompt as an Administrator.

1.  [Install Chocolatey](https://chocolatey.org/install).

    ```cmd
    @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
    ```

1.  Verify Chocolatey was added to the environment variables:

    -  In the Windows UI, open search and type `path`.
    -  In the Windows CMD console, type `echo %path%`.
    
    You should see `C:\ProgramData\chocolatey\bin` in the path.

1.  Close and reopen the command prompt before using `choco` commands.

After running the script at the command line, you can install any required extensions. Chocolately has many extensions available, similar to Homebrew for Mac OS. As a best practice, only use extensions labeled as a "trusted package".

### Install Ruby extension

If you have Ruby installed on the workstation, then you can skip this installation.

1.  In the CMD console, install the ruby extension:

    ```cmd
    choco install ruby
    ```

1.  Verify the environment variables were added properly:

    -  In the Windows UI, open search and type `path`.
    -  In the Windows CMD console, type `echo %path%`.

>  **NOTE**  
>  If you encounter problems with ruby, or the `gem` command is not recognized, you can install the `rubyinstaller-devkit.exe` development kit located in the `c:\ProgramData\chocolatey\bin` folder.

## Connect the repository

You may have to close and reopen the Git Bash application after the Choco installations.

1.  Open Git Bash.

1.  In the directory you created for Git repositories, clone the DevDocs repository.

    ```bash
    git clone <devdocs>
    ```

1.  Change to the `devdocs` directory.

1.  Install Bundler.

    ```bash
    gem install bundle
    ```

1.  Install gem executables for building the site, such as Jekyll.

    ```bash
    bundle install
    ```

1.  Build site.

    ```bash
    bundle exec jekyll serve
    ```

    ```terminal
    Configuration file: C:/Users/Administrator/mage/devdocs/_config.yml
                Source: C:/Users/Administrator/mage/devdocs
           Destination: C:/Users/Administrator/mage/devdocs/_site
     Incremental build: disabled. Enable with --incremental
          Generating...
                        done in 643.551 seconds.
     Auto-regeneration: enabled for 'C:/Users/Administrator/mage/devdocs'
        Server address: http://127.0.0.1:4000/
      Server running... press ctrl-c to stop.
    ```

>  **NOTE**  
>  The .bash_profile CAN be created and managed using Git Bash for aliases and other customizations. It sits in the 
`users/Administrator` folder.
