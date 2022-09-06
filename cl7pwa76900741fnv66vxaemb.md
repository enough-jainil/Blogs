## Developers Update August 2022

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1662450706368/h9A8AHYZg4.png).png)

![Developers Update August 2022](https://cdn.hashnode.com/res/hashnode/image/upload/v1662450708782/6xfz866PU.png).png?w=1290&ssl=1 "Developers Update August 2022 9")

10 malicious packages on PyPI
-----------------------------

### What is PyPI?

PyPI Means The Python Package Index like in JS We use Npm (Node Package Manager) from where we can use and install third-party packages easily and like that for python we have PyPI.

### Malicious Packages

The developers have told that in PyPI where python packages are available, 10 packages are used to steal the data of the users. means they are malicious

If you are still using these 10 packages in your project then immediately switch to another or remove them from the project

The researchers provide details about the malicious packages:

*   **[Ascii2text](https://pypi.org/project/ascii2text/)** is a malicious package that mimics the popular art [package](https://pypi.org/project/art/) by name and description. The code on the **init**.py file downloads and executes a malicious script that searches for local passwords and uploads them using a discord webhook.
*   **[Pyg-utils](https://pypi.org/project/pyg-utils/), [Pymocks](https://pypi.org/project/pymocks/) and [PyProto2](https://pypi.org/project/PyProto2/)** are malicious packages that allow attackers to steal users’ AWS credentials.
*   **[Free-net-vpn](https://pypi.org/project/free-net-vpn/)** and **[Free-net-vpn2](https://pypi.org/project/free-net-vpn2/)** are malicious packages developed to target environment variables.
*   **[Test-async](https://pypi.org/project/test-async)** downloads and executes malicious payloads.
*   **[Zlibsrc](https://pypi.org/project/zlibsrc/)** downloads and executes malicious payloads.
*   **[Free-net-vpn](https://pypi.org/project/free-net-vpn/)** and **[Free-net-vpn2](https://pypi.org/project/free-net-vpn2/)** are malicious packages that target environment variables.
*   **[WINRPCexploit](https://pypi.org/project/WINRPCexploit/)** is a malicious package that steals users’ credentials as part of its [setup.py](http://setup.py) installation script.
*   **[Browserdiv](https://pypi.org/project/browserdiv/#files)** can steal the installer’s credentials by collecting and sending them to a predefined discord webhook.

Updates for Deno
----------------

### What is Deno?

Based on the V8 JavaScript engine and the Rust programming language, Deno is a runtime for JavaScript, TypeScript, and WebAssembly.

### Now What is Changing in Deno.

Long ago when this Deno came, it was very famous. But there is this one limitation we cannot install Npm packages in Deno so according to Ryan Dahl Within the next three months, Deno will be updated to make it possible to quickly import npm packages and support 80.99% of npm packages.

Example of importing in Deno

    import express from "npm:express@5"

The majority of npm modules will be able to be added as dependencies in the next three months. The packages will be downloaded automatically and stored in the Deno cache; there won’t be a node\_modules folder or npm installation.

Quite GitHub
------------

The (Software Freedom Conservancy) has left and encourages other developers to do the same.

The main reason for it is **GitHub copilot** and how **GitHub/Microsoft refused/delayed answering the questions** asked by SFC.

SFC launched a website to quit Github [Give Up GitHub – Software Freedom Conservancy (sfconservancy.org)](https://sfconservancy.org/GiveUpGitHub/)

RUST Malware Leaked
-------------------

So what happened there is malware written in RUST which has been leaked in hacking forums its source code is leaked.

So now it is cleverly known that this malware, is very active. So the developers who were there told me that they had created this malware only in 6 hours. And this malware was attacking only the Windows system. After that Cybersecurity firm, Cyble analyzed the malware and named it Luca Stealer. Cyble found Luca Stealer “can target multiple Chromium-based browsers, chat applications, crypto wallets, and gaming applications and has the added functionality of stealing victims’ files.”

In total, Luca Stealer targets:

*   31 browsers,
*   17 password managers,
*   19 browser crypto wallets,
*   10 “cold” crypto wallets,
*   7 applications (Steam, ICQ, Telegram, Skype, Element, Discord, and Uplay)

VS Code Update
--------------

n July 2022 release of Visual Studio Code. There are many updates in this version that we hope you’ll like, some of the key highlights include:

*   **[Title bar customization](https://code.visualstudio.com/updates/v1_70#_easier-title-bar-customization)** – Hide/show the menu bar, Command Center, or layout control.
*   **[Fold selection](https://code.visualstudio.com/updates/v1_70#_fold-selection)** – Create your own folded regions in the editor.
*   **[Search multi-select](https://code.visualstudio.com/updates/v1_70#_search-multiple-selection)** – Select and then act on multiple search results.
*   **[Tree view search and filtering](https://code.visualstudio.com/updates/v1_70#_tree-find-control)** – Find and filter in tree views such as the Find Explorer.
*   **[Terminal improvements](https://code.visualstudio.com/updates/v1_70#_terminal)** – Shell integration on by default, extended PowerShell keybindings.
*   **[Command line option –merge](https://code.visualstudio.com/updates/v1_70#_command-line-option-merge)** – Use the 3-way merge editor as your default merge tool.
*   **[Notebooks: Go to Most Recently Failed Cell](https://code.visualstudio.com/updates/v1_70#_go-to-most-recently-failed-cell)** – Jump directly to notebook errors.
*   **[Python Get started experience](https://code.visualstudio.com/updates/v1_70#_python)** – Quickly install and configure Python within VS Code.
*   **[Sticky scroll preview](https://code.visualstudio.com/updates/v1_70#_editor-sticky-scroll)** – New scrolling UI shows the current source code scope.
*   **[Dev container CLI topic](https://code.visualstudio.com/updates/v1_70#_development-container-cli)** – Learn about the updated development container CLI.

Twitter Dall.e
--------------

### What is Dall.e?

DALLE, the Al system that creates realistic images and art from a description in natural language is now available in beta.

WhatsApp Update
---------------

WhatsApp recently released 3 major Updates on leaving groups, screenshots in one-time shares and many more.

### What’s new?

**Exit Groups Silently**

Users can now quietly leave groups on WhatsApp without informing anyone. When a member leaves the group, only the group administrators will be informed. There will be no alerts for the remaining group members. This month, all users worldwide will start receiving the feature, according to WhatsApp.

**Who Can See Your Online Status**

who can view your online status With the upcoming features, WhatsApp, which is owned by Meta, is taking every precaution to protect content, which has been one of the platform’s main privacy concerns. Users have occasionally wished they could conceal their online presence on the platform to avoid awkward situations with people they don’t want to communicate with.

WhatsApp is now offering the option to control who can and cannot see when you’re online, which is useful for those times when you want to keep your online activity private.

**Prevent users from screenshotting “view once” messages**

In the past, WhatsApp introduced “View Once,” which is already a hugely popular way to share photos or other types of media on the platform without creating a permanent digital record. As of today, WhatsApp will enable screenshot blocking for “View Once” messages as an additional layer of security.

To give users more options for securing their messages, WhatsApp has continuously added new layers of privacy protection. These include self-destructing messages that vanish, end-to-end encrypted backups for when you want to save your chat history, 2-step verification for increased security, and the ability to block and report unwanted chats.

Microsoft 3D Emoji
------------------

Finally, Microsoft 3D Emoji is now an open source which means you can now use emojis in your project

Here are some links for it…[GitHub](https://github.com/microsoft/fluentui-emoji)

Remix accused Solid JS
----------------------

### What is Remix?

The remix is a full-stack, edge-first framework that enables developers to design wonderful user experiences with a focus on web standards. You can use it to build your web application and use JavaScript and React for both client-side and server-side rendering.

#### Accusation

Remix accused Solid JS of copying its documentation by just changing its name and logo in the documentation and Solid JS accepted that it was their fault and said that it was done just for testing purposes.

> On behalf of Solid Core we apologize. The intent was to temporarily use copy for practically prototyping the new docs infrastructure. There was no intent to publish this as our own, especially without credit. Note: the writing process hasn't officially started for SolidStart 1/4 [https://t.co/78K5v27Tjz](https://t.co/78K5v27Tjz)
> 
> — David Di Biase (@davedbase) [August 10, 2022](https://twitter.com/davedbase/status/1557422052679815173?ref_src=twsrc%5Etfw)

So this is the update from August if you like this post please share it with your friends and your developer partner.

<p>The post [Developers Update August 2022](https://jainil.dev/developers-update-august-2022/) first appeared on [Jainil Prajapati.](https://jainil.dev).</p>