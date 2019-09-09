# SearchSploit.py
Independant repo to my fork of exploitdb
# The Exploit Database Git Repository

This is an unofficial repository of [The Exploit Database](https://www.exploit-db.com/), a [project](https://www.offensive-security.com/community-projects/) sponsored by [Offensive Security](https://www.offensive-security.com/).
Our repositories are:

  - Exploits & Shellcodes: [https://github.com/offensive-security/exploitdb](https://github.com/offensive-security/exploitdb)
  - Binary Exploits: [https://github.com/offensive-security/exploitdb-bin-sploits](https://github.com/offensive-security/exploitdb-bin-sploits)
  - Papers: [https://github.com/offensive-security/exploitdb-papers](https://github.com/offensive-security/exploitdb-papers)

Each needs to be manually pulled first and places into the settings file.

The Exploit Database is an archive of public exploits and corresponding vulnerable software, developed for use by penetration testers and vulnerability researchers. Its aim is to serve as the most comprehensive collection of [exploits](https://www.exploit-db.com/browse/), [shellcode](https://www.exploit-db.com/shellcode/) and [papers](https://www.exploit-db.com/papers/) gathered through direct submissions, mailing lists, and other public sources, and present them in a freely-available and easy-to-navigate database. The Exploit Database is a repository for exploits and Proof-of-Concepts rather than advisories, making it a valuable resource for those who need actionable data right away.
You can learn more about the project [here (about)](https://www.exploit-db.com/about-exploit-db/) and [here (history)](https://www.exploit-db.com/history/).

This repository is updated daily with the most recently added submissions. Any additional resources can be found in our [binary exploits repository](https://github.com/offensive-security/exploitdb-bin-sploits).


- - -

## License

This project (and SearchSploit) is released under "[GNU General Public License v2.0](https://github.com/offensive-security/exploitdb/blob/master/LICENSE.md)".

- - -

# SearchSploit

Included with this repository is the **SearchSploit** utility, which will allow you to search through exploits, shellcodes and papers _(if installed)_ using one or more terms.
For more information, please see the **[SearchSploit manual](https://www.exploit-db.com/searchsploit/)**.

## Usage/Example

```
root@kali:~# searchsploit -h
  Usage: searchsploit [options] term1 [term2] ... [termN]

==========
 Examples
==========
  searchsploit afd windows local
  searchsploit -t oracle windows
  searchsploit -p 39446
  searchsploit linux kernel 3.2 --exclude="(PoC)|/dos/"
  searchsploit linux reverse password

  For more examples, see the manual: https://www.exploit-db.com/searchsploit/

=========
 Options
=========
   -c, --case     [Term]      Perform a case-sensitive search (Default is inSEnsITiVe).
   -e, --exact    [Term]      Perform an EXACT match on exploit title (Default is AND) [Implies "-t"].
   -h, --help                 Show this help screen.
   -j, --json     [Term]      Show result in JSON format.
   -m, --mirror   [EDB-ID]    Mirror (aka copies) an exploit to the current working directory.
   -o, --overflow [Term]      Exploit titles are allowed to overflow their columns.
   -p, --path     [EDB-ID]    Show the full path to an exploit (and also copies the path to the clipboard if possible).
   -t, --title    [Term]      Search JUST the exploit title (Default is title AND the file's path).
   -u, --update               Check for and install any exploitdb package updates (deb or git).
   -w, --www      [Term]      Show URLs to Exploit-DB.com rather than the local path.
   -x, --examine  [EDB-ID]    Examine (aka opens) the exploit using $PAGER.
       --colour               Disable colour highlighting in search results.
       --id                   Display the EDB-ID value rather than local path.
       --nmap     [file.xml]  Checks all results in Nmap's XML output with service version (e.g.: nmap -sV -oX file.xml).
                                Use "-v" (verbose) to try even more combinations
       --exclude="term"       Remove values from results. By using "|" to separated you can chain multiple values.
                                e.g. --exclude="term1|term2|term3".

=======
 Notes
=======
 * You can use any number of search terms.
 * Search terms are not case-sensitive (by default), and ordering is irrelevant.
   * Use '-c' if you wish to reduce results by case-sensitive searching.
   * And/Or '-e' if you wish to filter results by using an exact match.
 * Use '-t' to exclude the file's path to filter the search results.
   * Remove false positives (especially when searching using numbers - i.e. versions).
 * When updating or displaying help, search terms will be ignored.

root@kali:~#
root@kali:~# searchsploit afd windows local
---------------------------------------------------------------------------------------- -----------------------------------
 Exploit Title                                                                          |  Path
                                                                                        | (/usr/share/exploitdb/)
---------------------------------------------------------------------------------------- -----------------------------------
Microsoft Windows (x86) - 'afd.sys' Local Privilege Escalation (MS11-046)               | exploits/windows_x86/local/40564.c
Microsoft Windows - 'AfdJoinLeaf' Local Privilege Escalation (MS11-080) (Metasploit)    | exploits/windows/local/21844.rb
Microsoft Windows - 'afd.sys' Local Kernel (PoC) (MS11-046)                             | exploits/windows/dos/18755.c
Microsoft Windows 7 (x64) - 'afd.sys' Dangling Pointer Privilege Escalation (MS14-040)  | exploits/windows_x86-64/local/39525.py
Microsoft Windows 7 (x86) - 'afd.sys' Dangling Pointer Privilege Escalation (MS14-040)  | exploits/windows_x86/local/39446.py
Microsoft Windows XP - 'afd.sys' Local Kernel Denial of Service                         | exploits/windows/dos/17133.c
Microsoft Windows XP/2003 - 'afd.sys' Local Privilege Escalation (K-plugin) (MS08-066)  | exploits/windows/local/6757.txt
Microsoft Windows XP/2003 - 'afd.sys' Local Privilege Escalation (MS11-080)             | exploits/windows/local/18176.py
---------------------------------------------------------------------------------------- -----------------------------------
Shellcodes: No Result
root@kali:~#
root@kali:~# searchsploit -p 39446
  Exploit: Microsoft Windows 7 (x86) - 'afd.sys' Dangling Pointer Privilege Escalation (MS14-040)
      URL: https://www.exploit-db.com/exploits/39446/
     Path: /usr/share/exploitdb/exploits/windows_x86/local/39446.py
File Type: Python script, ASCII text executable, with CRLF line terminators

Copied EDB-ID #39446's path to the clipboard.
root@kali:~#
```

- - -

## Install

To install the application. you will need to update your .searchsploit_rc and possibly place a copy into your home directory.

The self updating function will require `git`, and the Nmap XML option to work, will require `beautifulsoup4` (found in the `python-beautifulsoup4` package in Debian-based systems).

You can find a **more in-depth guide in the [SearchSploit manual](https://www.exploit-db.com/searchsploit/)**.

**Git**

In short: clone the repository, add the binary into $PATH, and edit the config file to reflect the git path:

```
$ sudo git clone https://github.com/offensive-security/exploitdb.git /opt/exploitdb
$ sed 's|path_array+=(.*)|path_array+=("/opt/exploitdb")|g' /opt/exploitdb/.searchsploit_rc > ~/.searchsploit_rc
$ sudo ln -sf /opt/exploitdb/searchsploit /usr/local/bin/searchsploit
```

## Credit

The following people made this possible:

- [Offensive Security](https://www.offensive-security.com/)
- [Unix-Ninja](https://github.com/unix-ninja)
- [g0tmi1k](https://blog.g0tmi1k.com/)
