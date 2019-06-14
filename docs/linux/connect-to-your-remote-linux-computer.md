---
title: Připojení k cílovému systému Linux v sadě Visual Studio
description: Jak se připojit na vzdálený počítač s Linuxem nebo WSL v rámci sady Visual Studio C++ projektu.
ms.date: 06/11/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 4003a7387981b60d22f0344463d1729974d437a7
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042688"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Připojení k cílovému systému Linux v sadě Visual Studio

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

Možné konfigurace projektu Linux k cíli vzdáleném počítači nebo subsystému Windows pro Linux (WSL).

## <a name="connect-to-a-remote-linux-computer"></a>Připojení ke vzdálenému počítači s Linuxem

Při sestavování C++ projektu Linux pro vzdálený systém Linux (virtuální nebo fyzický počítač), Linux, se zkopíruje do vzdálenému počítači s Linuxem a potom zkompiluje kód podle nastavení sady Visual Studio. (V sadě Visual Studio 2017, použijte tyto pokyny pro připojení k WSL také. Použít **localhost** pro **název hostitele**.)

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

1. Klikněte na tlačítko **připojit** tlačítko pokusu o připojení ke vzdálenému počítači. 

   Pokud se připojování povede, Visual Studio se začne konfigurace používat vzdálených hlaviček IntelliSense. Další informace najdete v tématu [technologie IntelliSense pro záhlaví ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se nepovede, vstupní pole, které je potřeba změnit bude označeno červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   Přejděte na **nástroje > Možnosti > pro různé platformy > protokolování** povolení protokolování, které vám pomohou vyřešit problémy s připojením:

   ![Vzdálené přihlášení](media/remote-logging-vs2019.png)

   Protokoly obsahovat připojení, všechny příkazy, odeslané do vzdáleného počítače (jejich text, ukončovací kód a doba provádění) a všechny operace zápisu ze sady Visual Studio se chcete k prostředí. Protokolování funguje pro každý projekt CMake napříč platformami nebo Linuxu založené na MSBuild projektu v sadě Visual Studio.

   Můžete nakonfigurovat výstup přejděte do souboru nebo **protokolování pro různé platformy** podokně ve výstupním okně. Pro projekty založené na MSBuild Linuxu, příkazy ke vzdálenému počítači pomocí nástroje MSBuild nejsou směrovány ke **okno výstup** protože jsou emitovaný mimo proces. Místo toho se protokolují do souboru s předponou "msbuild_".

## <a name="connect-to-wsl"></a>Připojte se k WSL

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
[Deply, spouštění a ladění projektu Linux](deploy-run-and-debug-your-linux-project.md)<br />




