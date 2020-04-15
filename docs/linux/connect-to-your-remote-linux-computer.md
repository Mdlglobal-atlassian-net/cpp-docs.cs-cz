---
title: Připojení k cílovému systému Linux ve Visual Studiu
description: Jak se připojit ke vzdálenému počítači s Linuxem nebo windows subsystém pro Linux z evnitř projektu Visual Studio C++.
ms.date: 01/17/2020
ms.openlocfilehash: 624dce6bb05e4f4a961628e0c6f455e11c14dff8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364365"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Připojení k cílovému systému Linux ve Visual Studiu

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range="vs-2017"

Projekt Linuxu můžete nakonfigurovat tak, aby cílil na vzdálený počítač nebo na podsystém Windows pro Linux (WSL). Pro vzdálené počítače i pro WSL je třeba nastavit vzdálené připojení v sadě Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Projekt Linuxu můžete nakonfigurovat tak, aby cílil na vzdálený počítač nebo na podsystém Windows pro Linux (WSL). Pro vzdálený počítač je třeba nastavit vzdálené připojení v sadě Visual Studio. Chcete-li se připojit k wsl, přeskočte dopředu na část [Připojit k WSL.](#connect-to-wsl)

::: moniker-end

::: moniker range=">=vs-2017"

Při použití vzdáleného připojení, Visual Studio staví C++ Linux projekty na vzdáleném počítači. Nezáleží na tom, jestli je to fyzický počítač, virtuální počítač v cloudu nebo WSL.
Chcete-li vytvořit projekt, Visual Studio zkopíruje zdrojový kód do vzdáleného počítače Linux. Potom kód zkompiluje na základě nastavení sady Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 verze 16.5 a novější také podporuje zabezpečené, Federal Information Processing Standard (FIPS) 140-2 kompatibilní kryptografická připojení k linuxovým systémům pro vzdálený vývoj. Chcete-li použít připojení kompatibilní s FIPS, postupujte podle pokynů v [části Nastavení zabezpečeného vzdáleného linuxového vývoje kompatibilního s FIPS.](set-up-fips-compliant-secure-remote-linux-development.md)

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Nastavení serveru SSH ve vzdáleném systému

Pokud ssh ještě není nastavena a spuštěna na vašem systému Linux, nainstalujte jej následujícím postupem. Příklady v tomto článku používají Ubuntu 18.04 LTS se serverem OpenSSH verze 7.6. Nicméně, pokyny by měly být stejné pro všechny distro pomocí mírně poslední verzi OpenSSH.

1. V systému Linux nainstalujte a spusťte server OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Pokud chcete, aby se server ssh spouštěl automaticky při spuštění systému, povolte jej pomocí systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Nastavení vzdáleného připojení

1. V Sadě Visual Studio zvolte **Nástroje > Možnosti** na řádku nabídek a otevřete dialogové okno **Volby.** Pak vyberte **Cross Platform > Connection Manager** otevřete dialogové okno Connection Manager.

   Pokud jste připojení v sadě Visual Studio ještě nenastavili, otevře visual studio při prvním sestavení projektu dialogové okno Connection Manager.

1. V dialogovém okně Správce připojení zvolte tlačítko **Přidat** a přidejte nové připojení.

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou případech se zobrazí okno **Připojit ke vzdálenému systému.**

   ![Připojení ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Záznam | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, na který je spuštěna služba SSH, obvykle 22
   | **Uživatelské jméno**           | Uživatel k ověření jako
   | **Typ ověřování** | Heslo a soukromý klíč jsou podporovány
   | **Heslo**            | Heslo pro zadané uživatelské jméno
   | **Soubor soukromého klíče**    | Soubor soukromého klíče vytvořený pro připojení ssh
   | **Heslo**          | Přístupové heslo použité s výše vybraným soukromým klíčem

   Pro ověřování můžete použít heslo nebo soubor klíče a přístupové heslo. Pro mnoho scénářů vývoje je ověřování hesla dostatečné, ale soubory klíčů jsou bezpečnější. Pokud již máte pár klíčů, je možné jej znovu použít. V současné době Visual Studio podporuje pouze RSA a DSA klíče pro vzdálená připojení.

1. Chcete-li se pokusit o připojení ke vzdálenému počítači, zvolte tlačítko **Připojit.**

   Pokud je připojení úspěšné, Visual Studio nakonfiguruje intelliSense používat vzdálené záhlaví. Další informace naleznete v tématu [IntelliSense pro záhlaví ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se připojení nezdaří, jsou pole, která je třeba změnit, označena červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Pokud používáte soubory klíčů pro ověřování, ujistěte se, že cílový počítač Je Server SSH běží a nakonfigurován správně.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Protokolování pro vzdálená připojení

   Protokolování můžete povolit a pomoci tak vyřešit problémy s připojením. Na řádku nabídek vyberte **Nástroje > Možnosti**. V dialogovém okně **Možnosti** vyberte **Protokolování > příčná platforma**:

   ![Vzdálené protokolování](media/remote-logging-vs2019.png)

   Protokoly zahrnují připojení, všechny příkazy odeslané do vzdáleného počítače (jejich text, ukončovací kód a čas spuštění) a veškerý výstup z visual studia do prostředí. Protokolování funguje pro jakýkoli projekt CMake napříč platformami nebo projekt Linux založený na MSBuild v sadě Visual Studio.

   Výstup můžete nakonfigurovat tak, aby přešel do souboru nebo do **podokna Protokolování napříč platformami** v okně Výstup. Pro linuxové projekty založené na MSBuild nejsou příkazy MSBuild odeslané do vzdáleného počítače směrovány do **výstupního okna,** protože jsou vyzařovány mimo proces. Místo toho jsou zaznamenány do souboru s předponou "msbuild_".

## <a name="command-line-utility-for-the-connection-manager"></a>Nástroj příkazového řádku pro správce připojení  

**Visual Studio 2019 verze 16.5 nebo novější**: ConnectionManager.exe je nástroj příkazového řádku pro správu vzdálených vývojových připojení mimo Visual Studio. Je to užitečné pro úkoly, jako je zřizování nového vývojového počítače. Nebo ji můžete použít k nastavení sady Visual Studio pro průběžnou integraci. Příklady a úplný odkaz na příkaz ConnectionManager naleznete v [tématu ConnectionManager reference](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>Předávání portů TCP

Podpora Linuxu sady Visual Studio má závislost na předávání portů TCP. **Rsync** a **gdbserver** jsou ovlivněny, pokud je předávání portů TCP ve vzdáleném systému zakázáno. Pokud jste touto závislostí ovlivněni, můžete tento [lístek návrhu](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) přehlasovat v komunitě vývojářů.

rsync je používán jak msbuild-založené linuxové projekty a CMake [projekty kopírovat záhlaví ze vzdáleného systému do systému Windows pro použití IntelliSense](configure-a-linux-project.md#remote_intellisense). Pokud nelze povolit předávání portů TCP, zakažte automatické stahování vzdálených záhlaví. Chcete-li jej zakázat, použijte **nástroje > možnosti > cross platformy > Connection Manager > vzdálené záhlaví IntelliSense Manager**. Pokud vzdálený systém nemá povoleno přesměrování portů TCP, zobrazí se tato chyba při zahájení stahování vzdálených záhlaví pro technologii IntelliSense:

![Chyba záhlaví](media/port-forwarding-headers-error.png)

rsync je také používán podporou CMake sady Visual Studio ke kopírování zdrojových souborů do vzdáleného systému. Pokud nelze povolit předávání portů TCP, můžete použít sftp jako metodu zdroje vzdálené kopie. sftp je často pomalejší než rsync, ale nemá závislost na předávání portů TCP. Metodu zdroje vzdálené kopie můžete spravovat pomocí **vlastnosti remoteCopySourcesMethod** v [Editoru nastavení CMake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Pokud je přesměrování portů TCP ve vzdáleném systému zakázáno, zobrazí se chyba ve výstupním okně CMake při prvním vyvolání rsync.

![Chyba rsync](media/port-forwarding-copy-error.png)

gdbserver lze použít pro ladění na vložených zařízeních. Pokud nelze povolit předávání portů TCP, musíte použít gdb pro všechny scénáře vzdáleného ladění. gdb se používá ve výchozím nastavení při ladění projektů ve vzdáleném systému.

## <a name="connect-to-wsl"></a>Připojení k wsl

::: moniker-end

::: moniker range="vs-2017"

V sadě Visual Studio 2017 používáte stejné kroky pro připojení k WSL jako pro vzdálený počítač s Linuxem. Použijte **localhost** pro **název hostitele**.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 verze 16.1 přidal nativní podporu pro použití C++ s [Windows Subsystem pro Linux (WSL)](/windows/wsl/about). To znamená, že můžete přímo vytvářet a ladit místní instalaci WSL. Již není nutné přidávat vzdálené připojení nebo konfigurovat SSH. Podrobnosti o [instalaci WSL](/windows/wsl/install-win10) naleznete zde.

Chcete-li nakonfigurovat instalaci WSL pro práci s Visual Studio, budete potřebovat následující nástroje nainstalované: gcc nebo clang, gdb, make, ninja-build (vyžadováno pouze pro projekty CMake pomocí Visual Studio 2019 verze 16.6 nebo novější), rsync a zip. Můžete je nainstalovat na distribuce, které používají apt pomocí tohoto příkazu, který také nainstaluje kompilátor g++:

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

Další informace naleznete v [tématu Stažení, instalace a nastavení úlohy Linuxu](download-install-and-setup-the-linux-development-workload.md).

Pokud chcete nakonfigurovat projekt MSBuild pro WSL, přečtěte si informace [o konfiguraci linuxového projektu](configure-a-linux-project.md). Pokud chcete nakonfigurovat projekt CMake pro WSL, přečtěte si informace [o konfiguraci projektu Linux CMake](cmake-linux-project.md). Chcete-li postupovat podle podrobných pokynů pro vytvoření jednoduché konzolové aplikace s WSL, podívejte se na tento úvodní blogový příspěvek na [C++ s Visual Studio 2019 a Podsystémem Windows pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Viz také

[Konfigurace projektu Linuxu](configure-a-linux-project.md)\
[Konfigurace projektu Linux CMake](cmake-linux-project.md)\
[Nasazení, spuštění a ladění projektu Linuxu](deploy-run-and-debug-your-linux-project.md)\
[Konfigurace ladicích relací CMake](../build/configure-cmake-debugging-sessions.md)
