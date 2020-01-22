---
title: Připojení k cílovému systému Linux v aplikaci Visual Studio
description: Jak se připojit ke vzdálenému počítači se systémem Linux nebo k subsystému Windows pro Linux z projektu C++ v rámci sady Visual Studio.
ms.date: 01/17/2020
ms.openlocfilehash: d0065b63d7a81d3ae3d68b26184c88aca77f601c
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518215"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Připojení k cílovému systému Linux v aplikaci Visual Studio

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range="vs-2017"

Projekt se systémem Linux můžete nakonfigurovat tak, aby se zacílen na vzdálený počítač nebo podsystém Windows pro Linux (WSL). Pro vzdálené počítače i pro WSL musíte nastavit vzdálené připojení v sadě Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Projekt se systémem Linux můžete nakonfigurovat tak, aby se zacílen na vzdálený počítač nebo podsystém Windows pro Linux (WSL). Pro vzdálený počítač je potřeba nastavit vzdálené připojení v sadě Visual Studio. Pokud se chcete připojit k WSL, přeskočte k části [připojit k WSL](#connect-to-wsl) .

::: moniker-end

::: moniker range=">=vs-2017"

Při použití vzdáleného připojení aplikace Visual Studio vytváří C++ na vzdáleném počítači projekty Linux. Nezáleží na tom, jestli se jedná o fyzický počítač, virtuální počítač v cloudu nebo WSL.
Pro sestavení projektu Visual Studio zkopíruje zdrojový kód do vzdáleného počítače se systémem Linux. Pak se kód zkompiluje na základě nastavení aplikace Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 verze 16,5 a novější podporuje také zabezpečená kryptografická připojení standardu FIPS (Federal Information Processing Standard 140-2), která vyhovují systémům Linux pro vzdálené vývoj. Chcete-li použít připojení kompatibilní se standardem FIPS, použijte místo toho postup v části [Nastavení bezpečného vzdáleného nasazení systému Linux kompatibilního se standardem FIPS](set-up-fips-compliant-secure-remote-linux-development.md) .

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Nastavení serveru SSH ve vzdáleném systému

Pokud se SSH ještě nenastavuje a neběží v systému Linux, nainstalujte ho podle těchto kroků. Příklady v tomto článku používají Ubuntu 18,04 LTS s OpenSSH serverem verze 7,6. Nicméně pokyny by měly být stejné pro všechny distribuce s využitím středně poslední verze OpenSSH.

1. V systému Linux nainstalujte a spusťte server OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Pokud byste chtěli, aby se server SSH spouštěl automaticky při spuštění systému, povolte ho pomocí systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Nastavení vzdáleného připojení

1. V aplikaci Visual Studio vyberte **nástroje > možnosti** na řádku nabídek a otevřete tak dialogové okno **Možnosti** . Pak vyberte pro **různé platformy > Správce připojení** a otevřete dialogové okno Správce připojení.

   Pokud jste ještě před prvním sestavením projektu nevytvořili připojení v sadě Visual Studio, Visual Studio otevře pro vás dialog Správce připojení.

1. V dialogovém okně Správce připojení kliknutím na tlačítko **Přidat** přidejte nové připojení.

   ![Správce připojení](media/settings_connectionmanager.png)

   V obou případech se zobrazí okno **připojit ke vzdálenému systému** .

   ![Připojit ke vzdálenému systému](media/connect.png)

1. Zadejte následující informace:

   | Entry | Popis
   | ----- | ---
   | **Název hostitele**           | Název nebo IP adresa cílového zařízení
   | **Port**                | Port, na kterém běží služba SSH, obvykle 22
   | **Uživatelské jméno**           | Uživatel, který se má ověřit jako
   | **Typ ověřování** | Heslo a privátní klíč jsou podporovány současně.
   | **Heslo**            | Heslo pro zadané uživatelské jméno
   | **Soubor privátního klíče**    | Soubor privátního klíče vytvořený pro připojení SSH
   | **Hesel**          | Přístupové heslo použité s privátním klíčem vybraným výše

   K ověřování můžete použít buď heslo, nebo soubor klíče a přístupové heslo. Pro mnoho scénářů vývoje je ověřování hesla dostatečné, ale soubory klíčů jsou bezpečnější. Pokud už máte pár klíčů, je možné ho znovu použít. V současné době Visual Studio podporuje jenom klíče RSA a DSA pro vzdálená připojení.

1. Klikněte na tlačítko **připojit** a pokuste se připojit ke vzdálenému počítači.

   Pokud je připojení úspěšné, Visual Studio nakonfiguruje technologii IntelliSense na používání vzdálených hlaviček. Další informace najdete v tématu [IntelliSense pro hlavičky ve vzdálených systémech](configure-a-linux-project.md#remote_intellisense).

   Pokud se připojení nepovede, jsou vstupní pole, která je potřeba změnit, označená červeně.

   ![Chyba Správce připojení](media/settings_connectionmanagererror.png)

   Pokud používáte soubory klíčů pro ověřování, ujistěte se, že je server SSH cílového počítače spuštěný a správně nakonfigurovaný.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Protokolování pro vzdálená připojení

   Můžete povolit protokolování, které vám pomůžou řešit problémy s připojením. Na panelu nabídek vyberte možnost **nástroje > možnosti**. V dialogovém okně **Možnosti** vyberte možnost **protokolování > pro různé platformy**:

   ![Vzdálené protokolování](media/remote-logging-vs2019.png)

   Protokoly zahrnují připojení, všechny příkazy odeslané do vzdáleného počítače (jejich text, ukončovací kód a čas spuštění) a veškerý výstup ze sady Visual Studio do prostředí. Protokolování funguje pro libovolný projekt CMake pro různé platformy nebo pro linuxový projekt založený na MSBuildu v sadě Visual Studio.

   Výstup můžete nakonfigurovat tak, aby přešel do souboru nebo do podokna **protokolování pro různé platformy** v okně výstup. Pro projekty Linux založené na MSBuild nejsou příkazy MSBuild odeslané do vzdáleného počítače směrovány do **okno výstup** , protože jsou generovány mimo proces. Místo toho jsou protokolovány do souboru s předponou "msbuild_".

## <a name="command-line-utility-for-the-connection-manager"></a>Nástroj příkazového řádku pro správce připojení  

**Visual Studio 2019 verze 16,5 nebo novější**: ConnectionManager. exe je nástroj příkazového řádku pro správu připojení vzdáleného vývoje mimo sadu Visual Studio. Je vhodný pro úlohy, jako je například zřízení nového vývojového počítače. Nebo ho můžete použít k nastavení sady Visual Studio pro průběžnou integraci. Příklady a kompletní odkaz na příkaz ConnectionManager naleznete v tématu [ConnectionManager reference](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>Předávání portů TCP

Podpora pro Linux v systému Visual Studio je závislá na předávání portů TCP. **Rsync** a **gdbserver** mají vliv na to, jestli je ve vzdáleném systému zakázané předávání portů TCP. Pokud to ovlivněno touto závislostí, můžete tento [lístek s návrhem](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) poslat na komunitu vývojářů.

rsync se používají v projektech Linux založených na MSBuildu i v projektech CMake ke [kopírování hlaviček ze vzdáleného systému do Windows pro použití v IntelliSense](configure-a-linux-project.md#remote_intellisense). Pokud nemůžete povolit předávání portů TCP, zakažte automatické stahování vzdálených hlaviček. Pokud ho chcete zakázat, použijte **nástroje > možnosti > pro různé platformy > Správce připojení > vzdálené záhlaví IntelliSense správce**. Pokud na vzdáleném systému není zapnuté předávání portů TCP, zobrazí se tato chyba, když se spustí stahování vzdálených hlaviček pro technologii IntelliSense:

![Chyba hlaviček](media/port-forwarding-headers-error.png)

rsync je také používána podporou CMake sady Visual Studio ke kopírování zdrojových souborů do vzdáleného systému. Pokud nemůžete povolit předávání portů TCP, můžete jako metodu vzdálené kopie zdrojů použít SFTP. protokol SFTP je často pomalejší než rsync, ale nemá závislost na předávání portů TCP. Metodu vzdálené kopírování zdrojů můžete spravovat pomocí vlastnosti **remoteCopySourcesMethod** v [editoru nastavení cmake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Pokud je přesměrování portu TCP na vzdáleném systému zakázané, při prvním vyvolání rsync se v okně výstupu CMake zobrazí chyba.

![Chyba rsync](media/port-forwarding-copy-error.png)

gdbserver se dá použít k ladění na integrovaných zařízeních. Pokud nemůžete povolit předávání portů TCP, musíte použít GDB pro všechny scénáře vzdáleného ladění. GDB se ve výchozím nastavení používá při ladění projektů ve vzdáleném systému.

## <a name="connect-to-wsl"></a>Připojení k WSL

::: moniker-end

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
