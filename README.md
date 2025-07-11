# TechTools

### Here are some tips and tricks to make your life as a developer and dealing with technology easier on a daily basis.

## Summary:

- [Dealing with GitHub Repositories](#dealing-with-github-repositories)

  - [1. Empty repository on GitHub](#1-if-you-have-an-empty-repository-on-github-and-your-project-is-in-your-ide-vscode-for-example)
  - [2. don't have a repository created on GitHub](#2-if-you-dont-have-a-repository-created-on-github-just-the-project-in-your-ide-vscode-for-example)
    - [Method 1](#method-1)
    - [Method 2](#method-2)

- [3. Repository on GitHub with your project already made](#3-if-you-have-a-repository-on-github-with-your-project-already-made-and-you-want-to-bring-all-the-files-to-your-ide-vscode-for-example)

- [4. Installing the requirements for development in Windows 10/11](#4-installing-the-requirements-for-development-in-windows-1011)

- [Tools](#tools)

## Dealing with GitHub Repositories

### Make sure you have Git installed on your machine, if not, follow the link to install it: [GitHub Downloads](https://git-scm.com/downloads)<br>

### 1. If you have an **empty repository on GitHub** and your project is in your IDE (vscode for example).

##### Start a Local Git Repository:

```git
git init -b main
```

##### Add the Files to the "Staging":

```git
git add .
```

##### Commit the Files:

```git
git commit -m "Initial Commit"
```

##### Connect your Local Repository to the GitHub Repository:

```git
git remote add origin https://github.com/your-username/your-repository.git
```

##### Push your Changes to GitHub:

```git
git push -u origin main
```

#### Command Summary:

- `git push` : The command to push.
- `origin` : Which remote repository to push to. - `main` : Which branch to push to.
- `-u` : (or `--set-upstream` ) This is an important shortcut. It makes your local `main` branch "follow" the remote `main` branch. In practice, this means that the next time you want to push something, you can just type `git push` .

#### After the last command, Git may ask you for your GitHub username and password. Note: Nowadays, GitHub requires a Personal Access Token (PAT) instead of your regular password for terminal operations. If it asks for the password and yours doesn't work, you'll need to create a PAT and use it instead.

#### After that, refresh your repository page on GitHub and all your files will be there!

[Return to Top](#summary)

### 2. If you **don't have a repository created on GitHub**, just the project in your IDE (vscode for example).

### **Method 1**

##### Start a Local Git Repository:

```git
git init -b main
```

##### Add the Files to the "Staging":

```git
git add .
```

##### Commit the Files:

```git
git commit -m "Initial Commit"
```

##### Create a repository on GitHub

##### **IMPORTANT: Create an Empty Repository**

##### **To avoid conflicts, DO NOT check any of the initialization boxes:**

**- DO NOT check "Add a README file".**
**- DO NOT check "Add .gitignore".**
**- DO NOT check "Choose a license".**

##### Connect your Local Repository to the GitHub Repository:

```git
git remote add origin https://github.com/your-username/your-repository.git
```

##### Push your Changes to GitHub:

```git
git push -u origin main
```

[Return to Top](#summary)

### **Method 2**

##### Install GitHub CLI:

##### If you don't have it yet, follow the instructions at [cli.github.com](https://cli.github.com/) After installing, you'll need to authenticate once with the `gh auth login` command.

##### Run the Magic Command:

##### After you've made your local commits (the ` init` , ` add` , `commit` steps), run this single command in your terminal:

```git
gh repo create
```

##### Follow the Interactive Steps: The tool will ask you a few questions:

`Create a new repository on GitHub from this existing local repository?` -> Select **Yes.**
`Repository name` -> It suggests the name of your current folder (press Enter to confirm). `Description` -> **Optional.**
`Visibility` -> Choose **Public** or **Private.**
`Add a remote?` -> **Yes.**
`What should the remote be called?` -> `origin` (press Enter).
`Would you like to push all the commits from 'main' to 'origin/main'?` -> **Yes.**
By answering "Yes" to the last question, `gh` will create the repository on GitHub, add the `remote` and do the `push` for you. All in one step!

##### **Which one to choose?**

- Method 1 (Website): This is a great way to start, as the process is more visual and helps you understand the concepts of `remote` and `push` .
- Method 2 (CLI): Once you get used to it, this method is much faster and more efficient for everyday use.

##### Both paths will lead you to the same result. Choose the one that feels most comfortable to you right now!

[Return to Top](#summary)

### 3. If you have a **repository on GitHub with your project already made** and you want to bring all the files to your IDE (vscode for example).

##### Copy the URL of the repository on GitHub:

- Click the green `< > Code` button.
- In the HTTPS tab, copy the URL that appears. It usually ends with `.git` . For beginners, the HTTPS URL is the most recommended.

##### Run the git clone command:

```
git clone https://github.com/username/repository-name.git
```

##### Press Enter. Git will:

- Create a new folder with the same name as the repository (e.g. `repository-name` ).
- Download all the files and history of the project into it.
- Automatically configure the connection to the remote repository (the `origin` ).

##### Open the Project in VS Code:

```md
# 1. Go to the folder that git just created

cd repository-name

# 2. Open VS Code in this folder

code .
```

#### How can I continue updating my repository locally now?

##### Add the Files to the "Staging":

```git
git add .
```

##### Commit the Files:

```git
git commit -m "Initial Commit"
```

##### Push your Changes to GitHub:

```git
git push -u origin main
```

[Return to Top](#summary)

## 4. Installing the requirements for development in Windows 10/11

### 1. Preparing the work environment

Click on the search bar (Search) next to the start button and type: powershell
Click on the "Run as administrator" option
Inform the user with administrative privileges and respective password
A window with the title: "Administrator: Windows PowerShell" will be available.
This is where we will execute the other commands

#### 1.1. Adjusting the execution permissions

Check the permissions configuration

> `Get-ExecutionPolicy`

If "Restricted" (Bypass or other information) appears, then type:

> `Set-ExecutionPolicy AllSigned`

Check the permissions again

> `Get-ExecutionPolicy AllSigned`

This confirms that we can proceed. If "AllSigned" does not appear, close the window and
repeat procedure 1 until successful. If you still have any questions, bring them to class.

### 2. Installing the necessary programs

#### 2.1. Installing the chocolatey package manager

Copy and paste the following content into the powershell terminal with administrator privileges and press ENTER

> `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`

After a few moments, the installation is complete.

Check the success of this step with:

> `choco --version 2.4.2`

Note: The version will be the same or newer.

#### 2.2. Installing VSCode (text editor with syntax highlighting)

> `choco install vscode -y`

#### 2.3. Installing Git (for use with GitHub)

> `choco install git.install -y`

**Requirements for developing applications in Python**

#### 2.4. Installing Python 3.13

> `choco install python313 -y`

**Requirements for Android**

#### 2.5. Installing Node.JS

> `choco install nodejs-lts -y`

#### 2.6. Installing Java 11

> `choco install openjdk11 -y`

#### 2.7. NodeJS version manager

> `choco install nvm -y`

#### 2.8. Alternative package manager to NPM (default)

> `choco install yarn -y`

[Return to Top](#summary)

## Tools

[Acesso remoto gratuito no navegador - openSource](https://www.dwservice.net)
<br>[AI: Alpaca - Canvas com tecnologia de IA para artistas digitais](https://www.alpacaml.com)
<br>[AI: Phind](https://www.phind.com)
<br>[AIDE: The open-source AI-native IDE](https://aide.dev)
<br>[Antivírus: Verificação online](https://www.virustotal.com/gui/home/upload)
<br>[Chrome browser ESP32 Installer](https://flasher.pdxlocs.com)
<br>[Cloud Guardrails: Quick reference to Cloud Best Practices](https://www.cloudguardrails.com)
<br>[Consulta IMEI para ver a situação de um aparelho celular](http://www.anatel.gov.br/celularlegal)
<br>[Criador de Flipbook Online com AI](https://fliphtml5.com)
<br>[CSV SQL Tool: Run queries directly in your browser](https://csvsqltool.com)
<br>[DEBUG: 67 Weird tricks your browser doesn't want you to know](https://alan.norbauer.com/articles/browser-debugging-tricks)
<br>[DESIGN Dribbble: Explore o trabalho de designers talentosos para seu próximo projeto](https://dribbble.com)
<br>[DETRAN: Transferência de documentos online](https://www.transferenciadigital.detran.sp.gov.br)
<br>[Download da imagem oficial do W11](https://www.microsoft.com/en-us/software-download/windows11)
<br>[Email obfuscation](https://www.albionresearch.com/tools/obfuscator)
<br>[Extrair texto de imagem](https://www.imagetotext.info/)
<br>[Ferramenta pra baixar conteúdos do Instagram](https://snapinsta.app/pt)
<br>[Ferramentas para manuseio de arquivos PDF](https://www.ilovepdf.com)
<br>[FrontendMasters: Your path to senior developer and beyond](https://frontendmasters.com) Gratuito
<br>[GitHub Student Developer Pack](https://education.github.com/pack) Gratuito
<br>[GO Playground](https://go.dev/play/) Teste seu código online
<br>[Google Colab: Permite escrever e executar Python no navegador](https://colab.research.google.com)
<br>[Google IDX: Ambiente de desenvolvimento online e/com banco de dados](https://idx.google.com)
<br>[GRUB: tunning/ajustes para deixar sua tela de inicialização incrível](https://www.edivaldobrito.com.br/mudar-o-visual-do-grub-com-o-tema-vimix/)
<br>[IA: Claude AI](https://claude.ai)
<br>[IA: Inteligência artificial brasileira](https://www.maritaca.ai)
<br>[IA: Perplexity: pesquise e descubra com IA](https://www.perplexity.ai)
<br>[Interview Coder - Assinatura USD](https://www.interviewcoder.co)
<br>[IP Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html)
<br>[Lista com os maiores programas em Shell do mundo](https://github.com/oils-for-unix/oils/wiki/The-Biggest-Shell-Programs-in-the-World) (e respectivos links)
<br>[Moshi IA: voice chat in English](https://moshi.chat/?queue_id=talktomoshi)
<br>[Obsidian: Ferramenta para anotação e vínculo de ideias com salvamento em arquivo texto](https://obsidian.md)
<br>[OCR: Document to Markdown com IA - OCR MUITO preciso](https://llamaocr.com)
<br>[One: a new React framework for web and native, built on Vite](https://onestack.dev)
<br>[Pinggy: Public URLs for Localhost, without downloading any binary](https://pinggy.io)
<br>[Pinterest Downloader](https://pinterestdownloader.com)
<br>[Pocketbase: Backend Open Source em um arquivo](https://pocketbase.io)
<br>[Podman: ferramenta gratuita para conteiners e kubernetes (docker)](https://podman-desktop.io)
<br>[SHAREM: framework de análise de shellcode com APIs e syscalls do Windows](https://github.com/Bw3ll/sharem)
<br>[Software Testing 101: A Beginner's Guide to Types and Techniques](https://www.linkedin.com/comm/pulse/software-testing-101-beginners-guide-types-techniques-wgphc) Gratuito
<br>[Verificador de Currículo/Resume Checker para interpretação em sistemas com IA](https://www.resumego.net/resume-checker/) Gratuito
<br>[VSCode Extension: Web Visual Editor - debug made easy](https://marketplace.visualstudio.com/items?itemName=Urin.vscode-web-visual-editor)
<br>[W11: Gerador de instalação limpa automática/offline](https://schneegans.de/windows/unattend-generator/)
<br>[W11: Winhance - Windows Enhancement Utility](https://github.com/memstechtips/Winhance)
<br>[Youtube Downloader](https://www.y2mate.com)

[Return to Top](#summary)
