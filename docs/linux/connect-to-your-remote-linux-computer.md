---
title: Připojení k cílovému systému Linux v aplikaci Visual Studio
description: Jak se připojit ke vzdálenému počítači se systémem Linux nebo k subsystému Windows pro Linux z projektu C++ v rámci sady Visual Studio.
ms.date: 11/09/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 4069979100c3b71a32e90ad72fb334d21a226e64
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755275"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Připojení k cílovému systému Linux v aplikaci Visual Studio

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Projekt se systémem Linux můžete nakonfigurovat tak, aby se zacílen na vzdálený počítač nebo podsystém Windows pro Linux (WSL). Pro vzdálené počítače a pro WSL v sadě Visual Studio 2017 je nutné nastavit vzdálené připojení.

## <a name="connect-to-a-remote-linux-computer"></a>Připojení ke vzdálenému počítači se systémem Linux

Při sestavování projektu pro C++ Linux pro vzdálený systém Linux (virtuální počítač nebo fyzický počítač) je zdrojový kód Linux zkopírován do vzdáleného počítače se systémem Linux. Pak se zkompiluje na základě nastavení sady Visual Studio.

Nastavení tohoto vzdáleného připojení:

1. Sestavte projekt poprvé. Případně můžete vytvořit novou položku ručně. Vyberte **nástroje > možnosti**, otevřete uzel **Správce připojení pro různé platformy >** a pak klikněte na tlačítko **Přidat** .

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou případech se zobrazí okno **připojit ke vzdálenému systému** .

   ![Připojit ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Entry | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Přístavní**                | Port, na kterém běží služba SSH, obvykle 22
   | **Uživatelské jméno**           | Uživatel, který se má ověřit jako
   | **Typ ověřování** | Heslo a privátní klíč jsou podporovány současně.
   | **Zadáno**            | Heslo pro zadané uživatelské jméno
   | **Soubor privátního klíče**    | Soubor privátního klíče vytvořený pro připojení SSH
   | **Hesel**          | Přístupové heslo použité s privátním klíčem vybraným výše

   K ověřování můžete použít buď heslo, nebo soubor klíče a přístupové heslo. Pro mnoho scénářů vývoje je ověřování heslem dostatečné. Pokud upřednostňujete použití souboru veřejného a privátního klíče, můžete vytvořit nový nebo [znovu použít stávající](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). V současné době jsou podporovány pouze klíče RSA a DSA.

   Privátní soubor klíčů RSA můžete vytvořit pomocí následujících kroků:

   1. Na počítači s Windows vytvořte pár klíčů ssh pomocí `ssh-keygen -t rsa`. Příkaz vytvoří veřejný klíč a privátní klíč. Ve výchozím nastavení umístí klíče pod `C:\Users\%USERNAME%\.ssh`s použitím názvů `id_rsa.pub` a `id_rsa`.

   1. Z Windows zkopírujte veřejný klíč do počítače se systémem Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

   1. V systému Linux přidejte klíč do seznamu autorizovaných klíčů (a ujistěte se, že soubor má správná oprávnění): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Klikněte na tlačítko **připojit** a pokuste se připojit ke vzdálenému počítači.

   Pokud je připojení úspěšné, spustí Visual Studio konfiguraci technologie IntelliSense pro použití vzdálených hlaviček. Další informace najdete v tématu [IntelliSense pro hlavičky ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se připojení nepovede, jsou vstupní pole, která je potřeba změnit, označená červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Pokud používáte soubory klíčů pro ověřování, ujistěte se, že je server SSH cílového počítače spuštěný a správně nakonfigurovaný.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Pokud chcete povolit protokolování, abyste mohli řešit problémy s připojením, přečtěte si **nástroje > možnosti > > protokolování pro různé platformy** .

   ![Vzdálené protokolování](media/remote-logging-vs2019.png)

   Protokoly zahrnují připojení, všechny příkazy odeslané do vzdáleného počítače (jejich text, ukončovací kód a čas spuštění) a veškerý výstup ze sady Visual Studio do prostředí. Protokolování funguje pro libovolný projekt CMake pro různé platformy nebo pro linuxový projekt založený na MSBuildu v sadě Visual Studio.

   Výstup můžete nakonfigurovat tak, aby přešel do souboru nebo do podokna **protokolování pro různé platformy** v okno výstup. Pro projekty Linux založené na MSBuild nejsou příkazy MSBuild odeslané do vzdáleného počítače směrovány do **okno výstup** , protože jsou generovány mimo proces. Místo toho jsou protokolovány do souboru s předponou "msbuild_".

## <a name="tcp-port-forwarding"></a>Předávání portů TCP

Podpora pro Linux v systému Visual Studio je závislá na předávání portů TCP. **Rsync** a **gdbserver** budou ovlivněny, pokud je ve vzdáleném systému zakázané předávání portů TCP. Pokud to ovlivněno touto závislostí, můžete tento [lístek s návrhem](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) poslat na komunitu vývojářů.

rsync se používají v projektech Linux založených na MSBuildu i v projektech CMake ke [kopírování hlaviček ze vzdáleného systému do Windows pro použití v IntelliSense](configure-a-linux-project.md#remote_intellisense). Pokud nemůžete povolit předávání portů TCP, zakažte automatické stahování vzdálených hlaviček. Pokud ho chcete zakázat, použijte **nástroje > možnosti > pro různé platformy > Správce připojení > vzdálené záhlaví IntelliSense správce**. Pokud na vzdáleném systému není zapnuté předávání portů TCP, zobrazí se tato chyba, když se spustí stahování vzdálených hlaviček pro technologii IntelliSense:

![Chyba hlaviček](media/port-forwarding-headers-error.png)

Rsync je také používána podporou CMake sady Visual Studio ke kopírování zdrojových souborů do vzdáleného systému. Pokud nemůžete povolit předávání portů TCP, můžete jako metodu vzdálené kopie zdrojů použít SFTP. protokol SFTP je často pomalejší než rsync, ale nemá závislost na předávání portů TCP. Metodu vzdálené kopírování zdrojů můžete spravovat pomocí vlastnosti **remoteCopySourcesMethod** v [editoru nastavení cmake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Pokud je přesměrování portu TCP na vzdáleném systému zakázané, při prvním vyvolání rsync se v okně výstupu CMake zobrazí chyba.

![Chyba rsync](media/port-forwarding-copy-error.png)

Gdbserver se dá použít k ladění na integrovaných zařízeních. Pokud nemůžete povolit předávání portů TCP, musíte použít GDB pro všechny scénáře vzdáleného ladění. GDB se ve výchozím nastavení používá při ladění projektů ve vzdáleném systému.

::: moniker-end

## <a name="connect-to-wsl"></a>Připojení k WSL

::: moniker range="vs-2017"

V aplikaci Visual Studio 2017 použijete stejný postup pro připojení k WSL při použití pro vzdálený počítač se systémem Linux. Pro **název hostitele**použijte **localhost** .

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 verze 16,1 přidala nativní podporu pro C++ použití s podsystémem [Windows pro Linux (WSL)](/windows/wsl/about). To znamená, že můžete vytvořit a ladit přímo na místní instalaci WSL. Už nemusíte přidávat vzdálené připojení ani konfigurovat SSH. Podrobnosti o [tom, jak nainstalovat WSL](/windows/wsl/install-win10) , najdete tady.

Chcete-li nakonfigurovat WSL instalaci pro práci se sadou Visual Studio, je třeba nainstalovat následující nástroje: RSZ, Clang, GDB, make, rsync a zip. Můžete je nainstalovat do distribuce, které používají APT, pomocí tohoto příkazu, který také nainstaluje kompilátor g + +:

```bash
sudo apt install g++ gdb make rsync zip
```

Další informace najdete v tématu [stažení, instalace a nastavení úlohy Linux](download-install-and-setup-the-linux-development-workload.md).

Chcete-li nakonfigurovat projekt MSBuild pro WSL, přečtěte si téma [konfigurace projektu pro Linux](configure-a-linux-project.md). Pokud chcete nakonfigurovat projekt CMake pro WSL, přečtěte si téma [konfigurace projektu Linux cmake](cmake-linux-project.md). Pokud chcete postupovat podle podrobných pokynů pro vytvoření jednoduché konzolové aplikace pomocí WSL, podívejte se na tento úvodní příspěvek na blogu v [ C++ článku Visual Studio 2019 a v subsystému Windows pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Viz také

[Konfigurace\ projektu pro Linux](configure-a-linux-project.md)
[Konfigurace projektu Linux cmake](cmake-linux-project.md)\
[Nasazení, spuštění a ladění projektu pro Linux](deploy-run-and-debug-your-linux-project.md)\
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)
