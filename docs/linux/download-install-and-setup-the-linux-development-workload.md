---
title: Instalace úlohy Linuxu pro C++ ve Visual Studiu
description: Popisuje, jak stáhnout, nainstalovat a nastavit linuxové úlohy pro C++ v sadě Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 8e10521ab35f3d85ced8bffd771b4e101d4d4fe6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364333"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Stažení, instalace a nastavení úlohy Linuxu

::: moniker range="vs-2015"

Linuxové projekty jsou podporované ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Pomocí ide sady Visual Studio v systému Windows můžete vytvářet, upravovat a ladit projekty jazyka C++, které se spouštějí na vzdáleném systému Linux, virtuálním počítači nebo [podsystému Windows pro Linux](/windows/wsl/about).

Můžete pracovat na existující základ kódu, který používá CMake bez nutnosti převést na projekt sady Visual Studio. Pokud je váš základ kódu napříč platformami, můžete cílit na Windows i Linux z Visual Studia. Můžete například upravit, sestavit a ladit kód v systému Windows pomocí sady Visual Studio a pak rychle znovu zacílit projekt pro Linux k sestavení a ladění v prostředí Linuxu. Soubory hlaviček Linuxu se automaticky zkopírují do místního počítače, kde je Visual Studio používá k poskytování úplné podpory Technologie IntelliSense (Dokončení výpisu, Přejít na definici a tak dále).

Pro všechny tyto scénáře je vyžadován vývoj Linuxu s úlohami **C++.**

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Nastavení sady Visual Studio

1. Do vyhledávacího pole systému Windows zadejte "Instalační služba sady Visual Studio":

   ![Vyhledávací pole systému Windows](media/visual-studio-installer-search.png)

1. Vyhledejte instalační program ve výsledcích **aplikace** a poklikejte na něj. Po otevření instalačního programu zvolte **Změnit**a klikněte na kartu **Úlohy.** Posuňte se dolů na **Jiné sady nástrojů** a vyberte vývoj Linuxu s úlohami **C++.**

   ![Úloha Visual C++ pro vývoj Linuxu](media/linuxworkload.png)

1. Pokud cílíte na IoT nebo vložené platformy, přejděte vpravo do podokna **Podrobnosti o instalaci.** V části **Vývoj Linuxu s C++** rozbalte **možnost Volitelné součásti**a vyberte součásti, které potřebujete. CMake podpora pro Linux je vybrána ve výchozím nastavení.

1. Chcete-li pokračovat v instalaci, klepněte na **tlačítko Změnit.**

## <a name="options-for-creating-a-linux-environment"></a>Možnosti pro vytvoření prostředí Linuxu

Pokud ještě nemáte počítač s Linuxem, můžete v Azure vytvořit virtuální počítač s Linuxem. Další informace najdete [v tématu Úvodní příručka: Vytvoření virtuálního počítače s Linuxem na webu Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

V systému Windows 10 můžete nainstalovat a cílit na svou oblíbenou distribuci Linuxu na podsystému Windows pro Linux (WSL). Další informace naleznete v [příručce K instalaci podsystému Windows pro Linux pro Windows 10](/windows/wsl/install-win10). Pokud nemáte přístup k Windows Storu, můžete [ručně stáhnout balíčky wsl distro](/windows/wsl/install-manual). WSL je pohodlné konzolové prostředí, ale nedoporučuje se pro grafické aplikace.

::: moniker-end

::: moniker range="vs-2019"

Linuxové projekty ve Visual Studiu vyžadují instalaci následujících závislostí do vzdáleného systému Linux nebo WSL:

- **Kompilátor** - Visual Studio 2019 má out-of-the-box podporu pro GCC a [Clang](/cpp/build/clang-support-cmake?view=vs-2019).
- **gdb** - Visual Studio automaticky spustí gdb v systému Linux a používá front-end ladicího programu Visual Studio k zajištění plné věrnosti ladění prostředí na Linuxu.
- **rsync** a **zip** - zahrnutí rsync a zip umožňuje Visual Studio extrahovat hlavičkové soubory z vašeho systému Linux do souborového systému Windows pro použití IntelliSense.
- **značka**
- **openssh-server** (pouze vzdálené linuxové systémy) - Visual Studio se připojuje ke vzdáleným linuxovým systémům přes zabezpečené připojení SSH.
- **CMake** (pouze projekty CMake) - Můžete nainstalovat [staticky propojené binární soubory CMake](https://github.com/microsoft/CMake/releases)společnosti Microsoft pro Linux .
- **ninja-build** (pouze projekty CMake)- [Ninja](https://ninja-build.org/) je výchozí generátor pro konfigurace Linuxu a WSL ve Visual Studiu 2019 verze 16.6 nebo novější.

Následující příkazy předpokládají, že používáte g++ místo clang.

::: moniker-end

::: moniker range="vs-2017"

Linuxové projekty ve Visual Studiu vyžadují instalaci následujících závislostí do vzdáleného systému Linux nebo WSL:

- **gcc** - Visual Studio 2017 má izvu podporu pro GCC.
- **gdb** - Visual Studio automaticky spustí gdb v systému Linux a používá front-end ladicího programu Visual Studio k zajištění plnohodnotného ladění v systému Linux.
- **rsync** a **zip** - zahrnutí rsync a zip umožňuje Visual Studio extrahovat hlavičkové soubory z vašeho systému Linux do souborového systému Windows pro IntelliSense.
- **značka**
- **openssh-server** - Visual Studio se připojuje ke vzdáleným linuxovým systémům přes zabezpečené připojení SSH.
- **CMake** (pouze projekty CMake) - Můžete nainstalovat [staticky propojené binární soubory CMake](https://github.com/microsoft/CMake/releases)společnosti Microsoft pro Linux .

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Nastavení Linuxu: Ubuntu na WSL

Při cílení wsl, není nutné přidávat vzdálené připojení nebo konfigurovat SSH za účelem sestavení a ladění. **zip** a **rsync** jsou vyžadovány pro automatickou synchronizaci linuxových hlaviček s podporou Visual Studia pro Intellisense. Pokud požadované aplikace ještě nejsou k dispozici, můžete je nainstalovat následujícím způsobem. **ninja-build** je vyžadován pouze pro projekty CMake.

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu na vzdálených systémech Linux

Cílový systém Linux musí mít **openssh-server**, **g++**, **gdb**, **ninja-build** (pouze projekty CMake) a **nainstalovat** a ssh daemon musí být spuštěn. **zip** a **rsync** jsou vyžadovány pro automatickou synchronizaci vzdálených hlaviček s místním počítačem pro podporu Intellisense. Pokud tyto aplikace ještě nejsou k dispozici, můžete je nainstalovat následujícím způsobem:

1. Na výzvu prostředí v počítači s Linuxem spusťte:

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   Můžete být vyzváni k zadání kořenového hesla z důvodu příkazu sudo.  Pokud ano, zadejte jej a pokračujte. Po dokončení jsou nainstalovány požadované služby a nástroje.

1. Ujistěte se, že služba ssh běží na vašem počítači s Linuxem spuštěním:

   ```bash
   sudo service ssh start
   ```

   Tím se spustí služba a spustí ji na pozadí, připraven přijmout připojení.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Fedora používá instalační program balíčku **DNF.** Chcete-li stáhnout **g++**, **gdb**, **make**, **rsync**, **ninja-build**a **zip**, spusťte:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

**zip** a **rsync** jsou vyžadovány pro automatickou synchronizaci linuxových hlaviček s podporou Visual Studia pro Intellisense. **ninja-build** je vyžadován pouze pro projekty CMake.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora na vzdálených systémech Linux

Cílový stroj se systémem Fedora používá instalační program balíčku **DNF.** Chcete-li stáhnout **openssh-server**, **g++**, **gdb**, **make**, **ninja-build**, **rsync**a **zip**a restartujte ssh daemon, postupujte podle těchto pokynů. **ninja-build** je vyžadován pouze pro projekty CMake.

1. Na výzvu prostředí v počítači s Linuxem spusťte:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   Můžete být vyzváni k zadání kořenového hesla z důvodu příkazu sudo.  Pokud ano, zadejte jej a pokračujte. Po dokončení jsou nainstalovány požadované služby a nástroje.

1. Ujistěte se, že služba ssh běží na vašem počítači s Linuxem spuštěním:

   ```bash
   sudo systemctl start sshd
   ```

   Tím se spustí služba a spustí ji na pozadí, připraven přijmout připojení.

::: moniker-end

::: moniker range="vs-2015"

Podpora vývoje Linuxu C++ je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

## <a name="next-steps"></a>Další kroky

Nyní jste připraveni vytvořit nebo otevřít projekt Linuxu a nakonfigurovat jej tak, aby běžel v cílovém systému. Další informace naleznete v tématu:

- [Vytvoření nového projektu Linux](create-a-new-linux-project.md)
- [Konfigurace projektu Linux CMake](cmake-linux-project.md)
