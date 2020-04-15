---
title: Konfigurace projektu C++ Linux v sadě Visual Studio
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 50d5df0e25e82238297458ec7fedb955654e525b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "80150963"
---
# <a name="configure-a-linux-project"></a>Konfigurace projektu Linux

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

Toto téma popisuje, jak nakonfigurovat projekt C++ Linux, jak je popsáno v [tématu Vytvoření nového projektu C++ Linux v sadě Visual Studio](create-a-new-linux-project.md). Projekty CMake Linux uvidíme [v tématu Konfigurace projektu Linux CMake](cmake-linux-project.md).

Projekt Linuxu můžete nakonfigurovat tak, aby cílil na fyzický počítač s Linuxem, virtuální počítač nebo [podsystém Windows pro Linux](/windows/wsl/about) (WSL).

::: moniker range="vs-2019"

**Visual Studio 2019 verze 16.1**:

- Při cílení na WSL se můžete vyhnout operacím kopírování, které jsou nezbytné pro vytváření a technologie IntelliSense při cílení na vzdálené systémy Linux.

- Můžete zadat samostatné cíle Linuxu pro vytváření a ladění.

::: moniker-end

## <a name="general-settings"></a>Obecná nastavení

Chcete-li zobrazit možnosti konfigurace, vyberte nabídku **Vlastnosti projektu >** nebo klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a v místní nabídce vyberte **Vlastnosti.** Zobrazí se **obecné** nastavení.

![Obecná konfigurace](media/settings_general.png)

Ve výchozím nastavení je vytvořen spustitelný soubor (.out). Chcete-li vytvořit statickou nebo dynamickou knihovnu nebo použít existující makefile, použijte nastavení **Typ konfigurace.**

Další informace o nastavení na stránkách vlastností naleznete v tématu [Linux Project Property Page Reference](prop-pages-linux.md).

## <a name="remote-settings"></a>Vzdálená nastavení

Chcete-li změnit nastavení týkající se vzdáleného počítače s Linuxem, nakonfigurujte vzdálená nastavení, která se zobrazí v části [Obecné](prop-pages/general-linux.md).

- Chcete-li určit vzdálený cílový počítač s Linuxem, použijte položku **Vzdáleného počítače sestavení.** To vám umožní vybrat jedno z dříve vytvořených připojení. Chcete-li vytvořit novou položku, přečtěte si část [Připojení ke vzdálenému počítači SR.](connect-to-your-remote-linux-computer.md)

   ![Sestavení stroje](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 verze 16.1**: Chcete-li cílit na podsystém Windows pro Linux, klikněte na šipku dolů pro **sadu nástrojů platformy** a zvolte **WSL_1_0**. Ostatní vzdálené možnosti zmizí a cesta k výchozímu prostředí WSL se zobrazí na jejich místě:

   ![WSL sestavení stroje](media/wsl-remote-vs2019.png)

   Pokud máte souběžné instalace WSL, můžete zde zadat jinou cestu. Další informace o správě více distribucí naleznete v [tématu Správa a konfigurace podsystému Windows pro Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Můžete zadat jiný cíl pro ladění na stránce > **Ladění** **vlastností konfigurace.**

   ::: moniker-end

- **Kořenový adresář vzdáleného sestavení** určuje kořenové umístění, kde je projekt postaven na vzdáleném počítači SIP. To bude výchozí **~/projekty,** pokud se nezmění.

- **Adresář projektu vzdáleného sestavení** je místo, kde bude tento konkrétní projekt postaven na vzdáleném počítači SIP. To bude výchozí **$(RemoteRootDir) /$(Název_projektu),** který se rozbalí do adresáře pojmenované ho po aktuálním projektu, pod kořenovým adresářem nastaveným výše.

> [!NOTE]
> Chcete-li změnit výchozí kompilátory jazyka C a C++ nebo linker a archivátor použitý k sestavení projektu, použijte příslušné položky v oddílu **C/C++ > obecné** a v části **Propojovací > Obecné.** Můžete například zadat určitou verzi GCC nebo Clang. Další informace naleznete [v tématu C/C++ Vlastnosti (Linux C++)](prop-pages/c-cpp-linux.md) a [Linker Vlastnosti (Linux C ++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Kopírovat zdroje (pouze vzdálené systémy)

::: moniker range="vs-2019"

Tato část se nevztahuje na cílení wsl.

::: moniker-end

Při sestavování vzdálených systémů jsou zdrojové soubory na vývojovém počítači zkopírovány do počítače S IP a tam kompilovány. Ve výchozím nastavení jsou všechny zdroje v projektu sady Visual Studio zkopírovány do umístění nastavených ve výše uvedených nastaveních. Do seznamu však lze také přidat další zdroje nebo zdroje kopírování lze zcela vypnout, což je výchozí pro projekt Makefile.

- **Zdroje ke kopírování** určují, které zdroje jsou zkopírovány do vzdáleného počítače. Ve výchozím nastavení ** \@(SourcesToCopyRemotely)** výchozí pro všechny soubory zdrojového kódu v projektu, ale neobsahuje žádné datové zdroje nebo soubory prostředků, jako jsou obrázky.

- **Zdroje kopírování** lze zapínat a vypínat a povolit a zakázat kopírování zdrojových souborů do vzdáleného počítače.

- **Další zdroje ke kopírování** umožňuje přidat další zdrojové soubory, které budou zkopírovány do vzdáleného systému. Můžete určit seznam oddělený středníkem nebo můžete použít syntaxi **:=** k určení místního a vzdáleného názvu, který chcete použít:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Vytváření událostí

Vzhledem k tomu, že všechny kompilace probíhá ve vzdáleném počítači (nebo WSL), několik dalších událostí sestavení byly přidány do sestavy události části vlastnosti projektu. Jedná **se o událost vzdáleného předběžného sestavení**, **vzdálenou událost před propojením**a **vzdálenou událost po sestavení**a dojde k ní ve vzdáleném počítači před nebo po jednotlivých krocích v procesu.

![Události sestavení](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a>Technologie IntelliSense pro záhlaví ve vzdálených systémech

Přidáte-li nové připojení v **programu Connection Manager**, aplikace Visual Studio automaticky rozpozná adresáře zahrnutí pro kompilátor ve vzdáleném systému. Visual Studio pak zipy nahoru a zkopíruje tyto soubory do adresáře v místním počítači se systémem Windows. Poté vždy, když použijete toto připojení v projektu Sady Visual Studio nebo CMake, záhlaví v těchto adresářích se používají k poskytování technologie IntelliSense.

> [!NOTE]
> Ve Visual Studiu 2019 verze 16.5 a novější byla optimalizována kopie vzdálené hlavičky. Záhlaví jsou nyní kopírovány na vyžádání při otevření projektu Linux nebo konfiguraci CMake pro cíl Linuxu. Kopie se vyskytuje na pozadí na základě projektu, na základě zadané kompilátory projektu. Další informace naleznete v [tématu Vylepšení přesnosti a výkonu linuxového technologie IntelliSense](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/).

Tato funkce závisí na tom, že linuxový počítač má nainstalovaný zip. Zip můžete nainstalovat pomocí tohoto příkazu apt-get:

```cmd
sudo apt install zip
```

Chcete-li spravovat mezipaměť záhlaví, přejděte na **nástroje > možnosti, > Správce připojení na příčce platformy > vzdálené hlavičky Správce IntelliSense Manager**. Chcete-li aktualizovat mezipaměť záhlaví po provedení změn v počítači s Linuxem, vyberte vzdálené připojení a pak vyberte **Aktualizovat**. Vyberte **Odstranit,** chcete-li záhlaví odebrat, aniž byste odstranili samotné připojení. Výběrem **možnosti Prozkoumat** otevřete místní adresář v **Průzkumníkovi souborů**. Považovat tuto složku za jen pro čtení. Chcete-li stáhnout záhlaví existujícího připojení, které bylo vytvořeno před visual studio 2017 verze 15.3, vyberte připojení a pak vyberte **Stáhnout**.

::: moniker range="vs-2017"

![Technologie IntelliSense vzdáleného záhlaví](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![Technologie IntelliSense vzdáleného záhlaví](media/connection-manager-vs2019.png)

Protokolování můžete povolit a pomoci tak při řešení problémů:

![Vzdálené protokolování](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Viz také

[Nastavení vlastností kompilátoru a sestavení](../build/working-with-project-properties.md)<br/>
[Obecné vlastnosti C++ (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Adresáře VC++ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Kopírovat zdroje vlastnosti projektu (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Vytváření vlastností událostí (Linux C++)](../linux/prop-pages/build-events-linux.md)
