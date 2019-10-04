---
title: Připojení k cílovému systému Linux v aplikaci Visual Studio
description: Jak se připojit ke vzdálenému počítači se systémem Linux nebo WSL zevnitř projektu sady Visual C++ Studio.
ms.date: 09/04/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 2f4e6311493f2b29ba6911ec1b76225b6c7abe6d
ms.sourcegitcommit: b85e1db6b7d4919852ac6843a086ba311ae97d40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71925562"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Připojení k cílovému systému Linux v aplikaci Visual Studio

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

Projekt se systémem Linux můžete nakonfigurovat tak, aby se zacílen na vzdálený počítač nebo podsystém Windows pro Linux (WSL). Pro vzdálené počítače a pro WSL v sadě Visual Studio 2017 je nutné nastavit vzdálené připojení. 

## <a name="connect-to-a-remote-linux-computer"></a>Připojení ke vzdálenému počítači se systémem Linux

Při sestavování projektu pro C++ Linux pro vzdálený systém Linux (virtuální počítač nebo fyzický počítač) se zdrojový kód Linux zkopíruje do vzdáleného počítače se systémem Linux a potom se zkompiluje na základě nastavení sady Visual Studio.

Nastavení tohoto vzdáleného připojení:

1. Sestavte projekt poprvé nebo vytvořte novou položku ručně, a to tak, že vyberete **nástroje > možnosti** a pak otevřete uzel **Správce připojení pro různé platformy >** a kliknete na tlačítko **Přidat** .

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou případech se zobrazí okno **připojit ke vzdálenému systému** .

   ![Připojit ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Entry | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Přístavní**                | Port, na kterém běží služba SSH, obvykle 22
   | **Uživatelské jméno**           | Uživatel, který se má ověřit jako
   | **Typ ověřování** | Heslo nebo privátní klíč jsou podporovány současně.
   | **Zadáno**            | Heslo pro zadané uživatelské jméno
   | **Soubor privátního klíče**    | Soubor privátního klíče vytvořený pro připojení SSH
   | **Hesel**          | Přístupové heslo použité s privátním klíčem vybraným výše

   Pro ověřování můžete použít buď heslo, nebo soubor klíče a přístupové heslo. Pro mnoho scénářů vývoje je ověřování heslem dostatečné. Pokud upřednostňujete použití souboru veřejného a privátního klíče, můžete vytvořit nový nebo [znovu použít stávající](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). V současné době jsou podporovány pouze klíče RSA a DSA. 
   
   Privátní soubor klíčů RSA můžete vytvořit pomocí následujících kroků:

    1. Na počítači s Windows vytvořte pár klíčů ssh s `ssh-keygen -t rsa`. Tím se vytvoří veřejný klíč a privátní klíč. Ve výchozím nastavení jsou klíče umístěny pod `C:\Users\%USERNAME%\.ssh` s názvy `id_rsa.pub` a `id_rsa`.

    1. Z Windows zkopírujte veřejný klíč do počítače se systémem Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

    1. V systému Linux přidejte klíč do seznamu autorizovaných klíčů (a ujistěte se, že soubor má správná oprávnění): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Kliknutím na tlačítko **připojit** se pokuste o připojení ke vzdálenému počítači. 

   Pokud je připojení úspěšné, spustí Visual Studio konfiguraci technologie IntelliSense pro použití vzdálených hlaviček. Další informace najdete v tématu [IntelliSense pro hlavičky ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se připojení nepovede, jsou vstupní pole, která je potřeba změnit, označená červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Pokud používáte klíčové soubory pro ověřování, ujistěte se, že je server SSH cílového počítače spuštěný a správně nakonfigurovaný.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Pokud chcete povolit protokolování, abyste mohli řešit problémy s připojením, přečtěte si **nástroje > možnosti > > protokolování pro různé platformy** .

   ![Vzdálené protokolování](media/remote-logging-vs2019.png)

   Protokoly zahrnují připojení, všechny příkazy odeslané do vzdáleného počítače (jejich text, ukončovací kód a čas spuštění) a veškerý výstup ze sady Visual Studio do prostředí. Protokolování funguje pro libovolný projekt CMake pro různé platformy nebo pro linuxový projekt založený na MSBuildu v sadě Visual Studio.

   Výstup můžete nakonfigurovat tak, aby přešel do souboru nebo do podokna **protokolování pro různé platformy** v okno výstup. Pro projekty Linux založené na platformě MSBuild nejsou příkazy vydané vzdálenému počítači nástrojem MSBuild směrovány do **okno výstup** , protože jsou generovány mimo proces. Místo toho jsou protokolovány do souboru s předponou "msbuild_".

   ::: moniker-end

## <a name="connect-to-wsl"></a>Připojení k WSL

::: moniker range="vs-2017"

V aplikaci Visual Studio 2017 se ke WSL připojujete pomocí stejných kroků jako připojení ke vzdálenému počítači se systémem Linux, jak je popsáno výše v tomto článku. Pro **název hostitele**použijte **localhost** .

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 verze 16,1 přidala nativní podporu pro C++ použití s podsystémem [Windows pro Linux (WSL)](https://docs.microsoft.com/windows/wsl/about).  To znamená, že už nebudete muset přidat vzdálené připojení nebo nakonfigurovat SSH, aby bylo možné sestavovat a ladit v místní instalaci WSL. Podrobnosti o [tom, jak nainstalovat WSL](https://docs.microsoft.com/windows/wsl/install-win10) , najdete tady.

Chcete-li nakonfigurovat WSL instalaci pro práci se sadou Visual Studio, je třeba nainstalovat následující nástroje: RSZ nebo Clang, GDB, make, rsync a zip. Můžete je nainstalovat do distribuce, které používají APT, pomocí tohoto příkazu, který také nainstaluje kompilátor g + +: 

```bash
sudo apt install g++ gdb make rsync zip
```
Další informace najdete v tématu [stažení, instalace a nastavení úlohy Linux](download-install-and-setup-the-linux-development-workload.md).

Pokud chcete nakonfigurovat projekt pro WSL, přečtěte si téma [konfigurace projektu pro Linux](configure-a-linux-project.md) nebo [konfigurace projektu pro Linux cmake](cmake-linux-project.md) v závislosti na tom, jaký druh projektu máte. Pokud chcete postupovat podle podrobných pokynů pro vytvoření jednoduché konzolové aplikace pomocí WSL, podívejte se na tento úvodní příspěvek na blogu v [ C++ článku Visual Studio 2019 a v subsystému Windows pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Viz také

[Konfigurace projektu Linux](configure-a-linux-project.md)<br />
[Konfigurace projektu Linux CMake](cmake-linux-project.md)<br />
[Nasazení, spuštění a ladění projektu pro Linux](deploy-run-and-debug-your-linux-project.md)<br />
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)
