---
title: Připojení k cílovému systému Linux v sadě Visual Studio
description: Jak se připojit na vzdálený počítač s Linuxem nebo WSL v rámci sady Visual Studio C++ projektu.
ms.date: 06/19/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 00d7facca2857efb0b8b43b5aaf38edce348a511
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861149"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Připojení k cílovému systému Linux v sadě Visual Studio

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

Můžete nakonfigurovat projekt systému Linux, který cílí na vzdáleném počítači nebo subsystému Windows pro Linux (WSL). Vzdálené počítače a WSL v sadě Visual Studio 2017 musíte nastavit připojení. 

## <a name="connect-to-a-remote-linux-computer"></a>Připojení ke vzdálenému počítači s Linuxem

Při sestavování C++ projektu Linux pro vzdálený systém Linux (virtuální nebo fyzický počítač), Linux, se zkopíruje do vzdálenému počítači s Linuxem a potom zkompiluje kód podle nastavení sady Visual Studio.

Nastavení tohoto vzdáleného připojení:

1. Prvním sestavení projektu nebo ručně vytvořit nový záznam výběrem **nástroje > Možnosti** a pak otevřete **různé platformy > Správce připojení** uzel a klikněte na tlačítko **přidat** tlačítko.

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou scénářích **připojit ke vzdálenému systému** zobrazí se okno.

   ![Připojit ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Entry | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, na kterém běží služba SSH na obvykle 22
   | **Uživatelské jméno**           | Ověření jako
   | **Typ ověřování** | Heslo nebo privátní klíč jsou podporované
   | **Heslo**            | Heslo pro zadané uživatelské jméno
   | **Souboru s privátním klíčem**    | Soubor privátního klíče vytvořené pro ssh připojení
   | **Přístupové heslo**          | Heslo s privátním klíčem výše vybraného

   Můžete buď heslo nebo klíč souborové služby a heslo pro ověření. Pro většinu scénářů vývoje stačí ověřování pomocí hesla. Pokud chcete použít soubor veřejného a privátního klíče, můžete vytvořit nový nebo [znovu použít existující](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Momentálně se podporuje jenom klíče RSA a DSA jsou podporovány. 
   
   Pomocí následujících kroků můžete vytvořit soubor privátního klíče RSA:

    1. Na počítači s Windows, vytvořte ssh dvojice klíčů s `ssh-keygen -t rsa`. Tím se vytvoří veřejný klíč a privátní klíč. Ve výchozím nastavení se umístí klíče `C:\Users\%USERNAME%\.ssh` s názvy `id_rsa.pub` a `id_rsa`.

    1. Z Windows, zkopírujte veřejný klíč pro počítač s Linuxem: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

    1. V systému Linux přidat do seznamu autorizovaných klíčů klíč (a ujistěte se, že soubor má správná oprávnění): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Klikněte na tlačítko **připojit** tlačítko pokusu o připojení ke vzdálenému počítači. 

   Pokud se připojování povede, Visual Studio se začne konfigurace používat vzdálených hlaviček IntelliSense. Další informace najdete v tématu [technologie IntelliSense pro záhlaví ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se nepovede, jsou uvedeny polí položky, které je potřeba změnit červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Pokud používáte soubory klíče pro ověřování, ujistěte se, že je server SSH cílovém počítači spuštěny a nakonfigurovány správně.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Přejděte na **nástroje > Možnosti > pro různé platformy > protokolování** povolení protokolování, které vám pomohou vyřešit problémy s připojením:

   ![Vzdálené přihlášení](media/remote-logging-vs2019.png)

   Protokoly obsahovat připojení, všechny příkazy, odeslané do vzdáleného počítače (jejich text, ukončovací kód a doba provádění) a veškerý výstup ze sady Visual Studio se chcete k prostředí. Protokolování funguje pro každý projekt CMake napříč platformami nebo Linuxu založené na MSBuild projektu v sadě Visual Studio.

   Můžete nakonfigurovat výstup přejděte do souboru nebo **protokolování pro různé platformy** podokně ve výstupním okně. Pro projekty založené na MSBuild Linuxu, příkazy ke vzdálenému počítači pomocí nástroje MSBuild nejsou směrovány ke **okno výstup** protože jsou emitovaný mimo proces. Místo toho se protokolují do souboru s předponou "msbuild_".

   ::: moniker-end

## <a name="connect-to-wsl"></a>Připojte se k WSL

::: moniker range="vs-2017"

V sadě Visual Studio 2017 připojíte se k WSL pomocí stejných kroků jako připojení ke vzdálenému počítači Linux, jak je popsáno výše v tomto článku. Použití **localhost** pro **název hostitele**.

::: moniker-end

::: moniker range="vs-2019"

V aplikaci Visual Studio 2019 verze 16.1 není nutné přidat připojení ke vzdálené nebo konfigurace SSH, pokud jsou cílem WSL. Vše, co se vyžaduje v systému Linux je gcc, gdb, ujistěte se, rsync a zip. Visual Studio vyžaduje rsync a zip pouze k extrahování hlavičkové soubory při prvním použití z vaší instance WSL do systému souborů Windows pro nástroj IntelliSense. Ve Visual Studio 2019 verze 16.1 je podpora WSL založená na Windows verze 1809. Může běžet na novější verzi Windows, ale Visual Studio ještě nevyužívá nových funkcí WSL.

Pokud vaše distribuce podporuje apt, můžete pomocí tohoto příkazu nainstalujte požadované balíčky:

```bash
sudo apt install g++ gdb make rsync zip
```

Konfigurace projektu pro WSL, naleznete v tématu [konfigurace projektu Linux](configure-a-linux-project.md) nebo [konfigurace projektu Linux CMake](cmake-linux-project.md) v závislosti na tom, jaký typ projektu máte.

::: moniker-end

## <a name="see-also"></a>Viz také

[Konfigurace projektu Linux](configure-a-linux-project.md)<br />
[Konfigurace projektu Linux CMake](cmake-linux-project.md)<br />
[Nasazení, spuštění a ladění projektu Linux](deploy-run-and-debug-your-linux-project.md)<br />




