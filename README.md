# 02-git-04-tools
Результаты выполнения Домашней Работы

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git show aefea
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
    Update CHANGELOG.md

----------------------------

2. Какому тегу соответствует коммит 85024d3?

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git show 85024d3
commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)


------------------------------------
3. Сколько родителей у коммита b8d720? Напишите их хеши.

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git show b8d720^
Продолжить?
commit b8d720f8340221f2146e4e4870bf2ee0bc48f2d5
Merge: 56cd7859e 9ea88f22f

или так

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log --graph b8d720
*   commit b8d720f8340221f2146e4e4870bf2ee0bc48f2d5
|\  Merge: 56cd7859e 9ea88f22f
| | Author: Chris Griggs <cgriggs@hashicorp.com>
| | Date:   Tue Jan 21 17:45:48 2020 -0800
| |
| |     Merge pull request #23916 from hashicorp/cgriggs01-stable
| |
| |     [Cherrypick] community links
| |
| * commit 9ea88f22fc6269854151c571162c5bcf958bee2b
|/  Author: Chris Griggs <cgriggs@hashicorp.com>
|   Date:   Tue Jan 21 17:08:06 2020 -0800
|
|       add/update community provider listings
|
*   commit 56cd7859e05c36c06b56d013b55a252d0bb7e158




---------------------------------------------------
4. Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24.

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log v0.12.23..v0.12.24
commit 33ff1c03bb960b332be3af2e333462dde88b279e (tag: v0.12.24)
Author: tf-release-bot <terraform@hashicorp.com>
Date:   Thu Mar 19 15:04:05 2020 +0000

    v0.12.24

^^^^^^^^^^^^^^^^^^^^^^^^^

commit b14b74c4939dcab573326f4e3ee2a62e23e12f89
Author: Chris Griggs <cgriggs@hashicorp.com>
Date:   Tue Mar 10 08:59:20 2020 -0700

    [Website] vmc provider links

commit 3f235065b9347a758efadc92295b540ee0a5e26e
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Thu Mar 19 10:39:31 2020 -0400

    Update CHANGELOG.md

commit 6ae64e247b332925b872447e9ce869657281c2bf
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Thu Mar 19 10:20:10 2020 -0400

    registry: Fix panic when server is unreachable

    Non-HTTP errors previously resulted in a panic due to dereferencing the
    resp pointer while it was nil, as part of rendering the error message.
    This commit changes the error message formatting to cope with a nil
    response, and extends test coverage.

    Fixes #24384

commit 5c619ca1baf2e21a155fcdb4c264cc9e24a2a353
Author: Nick Fagerlund <nick.fagerlund@gmail.com>
Date:   Wed Mar 18 12:30:20 2020 -0700

    website: Remove links to the getting started guide's old location

    Since these links were in the soon-to-be-deprecated 0.11 language section, I
    think we can just remove them without needing to find an equivalent link.

commit 06275647e2b53d97d4f0a19a0fec11f6d69820b5
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Wed Mar 18 10:57:06 2020 -0400

    Update CHANGELOG.md

commit d5f9411f5108260320064349b757f55c09bc4b80
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Tue Mar 17 13:21:35 2020 -0400

    command: Fix bug when using terraform login on Windows

commit 4b6d06cc5dcb78af637bbb19c198faff37a066ed
Author: Pam Selle <pam@hashicorp.com>
Date:   Tue Mar 10 12:04:50 2020 -0400

    Update CHANGELOG.md

commit dd01a35078f040ca984cdd349f18d0b67e486c35
Author: Kristin Laemmert <mildwonkey@users.noreply.github.com>
Date:   Thu Mar 5 16:32:43 2020 -0500

    Update CHANGELOG.md

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

commit 225466bc3e5f35baa5d07197bbc079345b77525e
Author: tf-release-bot <terraform@hashicorp.com>
Date:   Thu Mar 5 21:12:06 2020 +0000

    Cleanup after v0.12.23 release

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>


-----------------------------------------------------
5. Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...) (вместо троеточего перечислены аргументы).

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log -S"func providerSource" --oneline
5af1e6234 main: Honor explicit provider_installation CLI config when present
8c928e835 main: Consult local directories as potential mirrors of providers

смотрим оба комита

первый раз функция появляется в комите

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git show 8c928e835
commit 8c928e83589d90a031f811fae52a81be7153e82f
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Thu Apr 2 18:04:39 2020 -0700


её определение выглядит так:

+func providerSource(services *disco.Disco)


6. Найдите все коммиты в которых была изменена функция globalPluginDirs.

  - ищем файлы 

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git grep -c globalPluginDirs
commands.go:2
internal/command/cliconfig/config_unix.go:1
plugins.go:2

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>

   - далее просматриваем коммиты в файлах

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log -L :globalPluginDirs:commands.go
fatal: -L parameter 'globalPluginDirs' starting at line 1: no match

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log -L :globalPluginDirs:internal/command/cliconfig/config_unix.go
fatal: -L parameter 'globalPluginDirs' starting at line 1: no match

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log -L :globalPluginDirs:plugins.go

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
В этом коммите были изменения
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

commit 78b12205587fe839f10d946ea3fdc06719decb05
Author: Pam Selle <204372+pselle@users.noreply.github.com>
Date:   Mon Jan 13 16:50:05 2020 -0500

    Remove config.go and update things using its aliases

diff --git a/plugins.go b/plugins.go
--- a/plugins.go
+++ b/plugins.go
@@ -16,14 +18,14 @@
 func globalPluginDirs() []string {
        var ret []string
        // Look in ~/.terraform.d/plugins/ , or its equivalent on non-UNIX
-       dir, err := ConfigDir()
+       dir, err := cliconfig.ConfigDir()
        if err != nil {
                log.Printf("[ERROR] Error finding global config directory: %s", err)
        } else {
                machineDir := fmt.Sprintf("%s_%s", runtime.GOOS, runtime.GOARCH)
                ret = append(ret, filepath.Join(dir, "plugins"))
                ret = append(ret, filepath.Join(dir, "plugins", machineDir))
        }

        return ret
 }

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
В этом коммите были изменения
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

commit 52dbf94834cb970b510f2fba853a5b49ad9b1a46
Author: James Bardin <j.bardin@gmail.com>
Date:   Wed Aug 9 17:46:49 2017 -0400

    keep .terraform.d/plugins for discovery

diff --git a/plugins.go b/plugins.go
--- a/plugins.go
+++ b/plugins.go
@@ -16,13 +16,14 @@
 func globalPluginDirs() []string {
        var ret []string
        // Look in ~/.terraform.d/plugins/ , or its equivalent on non-UNIX
        dir, err := ConfigDir()
        if err != nil {
                log.Printf("[ERROR] Error finding global config directory: %s", err)
        } else {
                machineDir := fmt.Sprintf("%s_%s", runtime.GOOS, runtime.GOARCH)
+               ret = append(ret, filepath.Join(dir, "plugins"))
                ret = append(ret, filepath.Join(dir, "plugins", machineDir))
        }

        return ret
 }

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
В этом коммите были изменения
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

commit 41ab0aef7a0fe030e84018973a64135b11abcd70
Author: James Bardin <j.bardin@gmail.com>
Date:   Wed Aug 9 10:34:11 2017 -0400

    Add missing OS_ARCH dir to global plugin paths

    When the global directory was added, the discovery system still
    attempted to search for OS_ARCH subdirectories. It has since been
    changed only search explicit paths.

diff --git a/plugins.go b/plugins.go
--- a/plugins.go
+++ b/plugins.go
@@ -14,12 +16,13 @@
 func globalPluginDirs() []string {
        var ret []string
        // Look in ~/.terraform.d/plugins/ , or its equivalent on non-UNIX
        dir, err := ConfigDir()
        if err != nil {
                log.Printf("[ERROR] Error finding global config directory: %s", err)
        } else {
-               ret = append(ret, filepath.Join(dir, "plugins"))
+               machineDir := fmt.Sprintf("%s_%s", runtime.GOOS, runtime.GOARCH)
+               ret = append(ret, filepath.Join(dir, "plugins", machineDir))
        }

        return ret
 }

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
В этом коммите были изменения
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


commit 66ebff90cdfaa6938f26f908c7ebad8d547fea17
Author: James Bardin <j.bardin@gmail.com>
Date:   Wed May 3 22:24:51 2017 -0400

    move some more plugin search path logic to command

    Make less to change when we remove the old search path

diff --git a/plugins.go b/plugins.go
--- a/plugins.go
+++ b/plugins.go
@@ -16,22 +14,12 @@
 func globalPluginDirs() []string {
        var ret []string
-
-       // Look in the same directory as the Terraform executable.
-       // If found, this replaces what we found in the config path.
-       exePath, err := osext.Executable()
-       if err != nil {
-               log.Printf("[ERROR] Error discovering exe directory: %s", err)
-       } else {
-               ret = append(ret, filepath.Dir(exePath))
-       }
-
        // Look in ~/.terraform.d/plugins/ , or its equivalent on non-UNIX
        dir, err := ConfigDir()
        if err != nil {
                log.Printf("[ERROR] Error finding global config directory: %s", err)
        } else {
                ret = append(ret, filepath.Join(dir, "plugins"))
        }

        return ret
 }

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
В этом коммите функция была представлена ------------
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


commit 8364383c359a6b738a436d1b7745ccdce178df47
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Thu Apr 13 18:05:58 2017 -0700

    Push plugin discovery down into command package

    Previously we did plugin discovery in the main package, but as we move
    towards versioned plugins we need more information available in order to
    resolve plugins, so we move this responsibility into the command package
    itself.

    For the moment this is just preserving the existing behavior as long as
    there are only internal and unversioned plugins present. This is the
    final state for provisioners in 0.10, since we don't want to support
    versioned provisioners yet. For providers this is just a checkpoint along
    the way, since further work is required to apply version constraints from
    configuration and support additional plugin search directories.

    The automatic plugin discovery behavior is not desirable for tests because
    we want to mock the plugins there, so we add a new backdoor for the tests
    to use to skip the plugin discovery and just provide their own mock
    implementations. Most of this diff is thus noisy rework of the tests to
    use this new mechanism.

diff --git a/plugins.go b/plugins.go
--- /dev/null
+++ b/plugins.go
@@ -0,0 +16,22 @@
+func globalPluginDirs() []string {
+       var ret []string
+
+       // Look in the same directory as the Terraform executable.
+       // If found, this replaces what we found in the config path.
+       exePath, err := osext.Executable()
+       if err != nil {
+               log.Printf("[ERROR] Error discovering exe directory: %s", err)
+       } else {
+               ret = append(ret, filepath.Dir(exePath))
+       }
+
+       // Look in ~/.terraform.d/plugins/ , or its equivalent on non-UNIX
+       dir, err := ConfigDir()
+       if err != nil {
+               log.Printf("[ERROR] Error finding global config directory: %s", err)
+       } else {
+               ret = append(ret, filepath.Join(dir, "plugins"))
+       }
+
+       return ret
+}

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>



7. Кто автор функции synchronizedWriters?

(venv) C:\Users\Олег\PycharmProjects\New_Netology\HWork5>git log -S synchronizedWriters --oneline
bdfea50cc remove unused
fd4f7eb0b remove prefixed io
5ac311e2a main: synchronize writes to VT100-faker on Windows

в последнем коммите

+func synchronizedWriters(targets ...io.Writer)

Author: Martin Atkins <mart@degeneration.co.uk>

