---
title: Konfigurace projektu C++ pro Linux v aplikaci Visual Studio
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 1cfaeb6611a27af498325739271d4dba38581dd6
ms.sourcegitcommit: c53a3efcc5d51fc55fa57ac83cca796b33ae888f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960679"
---
# <a name="configure-a-linux-project"></a>Konfigurace projektu Linux

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

Toto téma popisuje, jak nakonfigurovat projekt C++ pro Linux, jak je popsáno v tématu [ C++ vytvoření nového projektu pro Linux v aplikaci Visual Studio](create-a-new-linux-project.md). Projekty CMake pro Linux najdete v tématu [konfigurace projektu Linux cmake ](cmake-linux-project.md). 

Můžete nakonfigurovat projekt pro Linux pro cíl fyzického počítače se systémem Linux, virtuálního počítače nebo subsystému [Windows pro Linux](/windows/wsl/about) (WSL). 

::: moniker range="vs-2019"

**Visual Studio 2019 verze 16,1**:

- Při cílení na WSL se můžete vyhnout operacím kopírování, které jsou nezbytné pro sestavování a IntelliSense při cílení na vzdálené systémy Linux.

- Pro sestavování a ladění můžete zadat samostatné cíle pro Linux.

::: moniker-end

## <a name="general-settings"></a>Obecné nastavení

Chcete-li zobrazit možnosti konfigurace, vyberte nabídku **Vlastnosti projektu >** nebo klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a v místní nabídce vyberte možnost **vlastnosti** . Zobrazí se **Obecné** nastavení.

![Obecná konfigurace](media/settings_general.png)

Ve výchozím nastavení je sestaven spustitelný soubor (. out). Chcete-li vytvořit statickou nebo dynamickou knihovnu nebo použít existující soubor pravidel, použijte nastavení **typ konfigurace** .

Další informace o nastaveních na stránkách vlastností naleznete v tématu [reference na stránku vlastností projektu platformy Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Vzdálená nastavení

Chcete-li změnit nastavení týkající se vzdáleného počítače se systémem Linux, nakonfigurujte Vzdálená nastavení, která se zobrazí pod položkou [Obecné](prop-pages/general-linux.md).

- Chcete-li zadat vzdálený cílový počítač se systémem Linux, použijte položku **vzdáleného počítače sestavení** . To vám umožní vybrat jedno z připojení, které jste vytvořili dříve. Chcete-li vytvořit novou položku, přečtěte si část [připojení ke vzdálenému počítači se systémem Linux](connect-to-your-remote-linux-computer.md) .

   ![Sestavit počítač](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 verze 16,1**: cílovou platformu Windows pro systém Linux získáte kliknutím na šipku dolů pro **sadu nástrojů platformy** a zvolením možnosti **WSL_1_0**. Ostatní možnosti vzdálené části zmizí a cesta k výchozímu prostředí WSL se zobrazí na svém místě:

   ![Počítač Build WSL](media/wsl-remote-vs2019.png)

   Pokud máte souběžné instalace WSL, můžete zde zadat jinou cestu. Další informace o správě více distribuce najdete v tématu [Správa a konfigurace subsystému Windows pro Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Můžete zadat jiný cíl pro ladění na stránce **vlastností konfigurace** > **ladění** .

   ::: moniker-end

- **Kořenový adresář vzdáleného sestavení** určuje kořenové umístění, kde je projekt sestaven na vzdáleném počítači se systémem Linux. Pokud se to nezmění, použije se výchozí hodnota **~/Projects** .

- **Adresář vzdáleného projektu sestavení** je, kde bude tento konkrétní projekt sestaven na vzdáleném počítači se systémem Linux. Ve výchozím nastavení se použije **$ (RemoteRootDir)/$ (ProjectName)** , které se rozšíří na adresář s názvem za aktuálním projektem v kořenovém adresáři, který jste výše nastavili.

> [!NOTE]
> Chcete-li změnit výchozí jazyk C++ C a kompilátory nebo linker a Archivační program použitý k sestavení projektu, použijte odpovídající položky v části **Obecné C/C++ > General** a **linker > General** . Můžete například zadat určitou verzi RSZ nebo Clang. Další informace naleznete v tématu [CC++ /Properties ( C++Linux)](prop-pages/c-cpp-linux.md) a [vlastnosti linkeru C++(Linux)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Kopírovat zdroje (pouze vzdálené systémy)

::: moniker range="vs-2019"

Tato část se nevztahuje na cílení na WSL.

::: moniker-end

Při sestavování vzdálených systémů se zdrojové soubory ve vývojovém počítači zkopírují do počítače se systémem Linux a kompiluje se tam. Ve výchozím nastavení se všechny zdroje v projektu sady Visual Studio zkopírují do umístění nastaveného v nastavení výše. Do seznamu je však možné přidat i další zdroje, nebo je možné také vypnout kopírování zdrojů, což je výchozí hodnota pro projekt makefile.

- **Zdroje ke kopírování** určují, které zdroje se zkopírují do vzdáleného počítače. Ve výchozím nastavení je **\@ (SourcesToCopyRemotely)** standardně všechny soubory zdrojového kódu v projektu, ale nezahrnuje žádné soubory assetů a prostředků, jako jsou například obrázky.

- Je možné zapnout nebo vypnout kopírování **zdrojů** a povolit nebo zakázat kopírování zdrojových souborů na vzdáleném počítači.

- **Další zdroje pro kopírování** vám umožní přidat další zdrojové soubory, které se zkopírují do vzdáleného systému. Můžete zadat seznam středníkem oddělených středníkem nebo můžete použít syntaxi **: =** k určení místního a vzdáleného názvu, který chcete použít:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Události sestavení

Vzhledem k tomu, že se na vzdáleném počítači (nebo WSL) koná veškerá kompilace, do oddílu události sestavení ve vlastnostech projektu byly přidány některé další události sestavení. Jedná se o **vzdálené události před sestavením**, **vzdálené události před propojením**a **vzdálené události po sestavení**a ke vzdálenému počítači dojde před nebo po jednotlivých krocích procesu.

![Události sestavení](media/settings_buildevents.png)

## <a name="remote_intellisense"></a>IntelliSense pro hlavičky ve vzdálených systémech

Když přidáte nové připojení ve **Správci připojení**, Visual Studio automaticky detekuje adresáře zahrnutí pro kompilátor ve vzdáleném systému. Visual Studio potom zips a zkopíruje tyto soubory do adresáře na místním počítači s Windows. Po každém použití tohoto připojení v projektu sady Visual Studio nebo CMake budou hlavičky v těchto adresářích použity k poskytnutí IntelliSense.

Tato funkce závisí na počítači se systémem Linux s nainstalovaným zip. Soubor zip můžete nainstalovat pomocí tohoto příkazu apt-get:

```cmd
sudo apt install zip
```

Pokud chcete spravovat mezipaměť hlaviček, přejděte na **nástroje > možnosti, > Správce připojení pro různé platformy > správce vzdáleného záhlaví IntelliSense**. Pokud chcete aktualizovat mezipaměť hlaviček po provedení změn v počítači se systémem Linux, vyberte vzdálené připojení a pak vyberte **aktualizovat**. Vyberte **Odstranit** pro odebrání hlaviček bez odstranění samotného připojení. Výběrem možnosti **prozkoumat** otevřete místní adresář v **Průzkumníkovi souborů**. Považovat tuto složku za jen pro čtení. Chcete-li stáhnout hlavičky pro existující připojení, které bylo vytvořeno před verzí sady Visual Studio 2017 verze 15,3, vyberte připojení a pak vyberte **Stáhnout**.

::: moniker range="vs-2017"

![Vzdálená hlavička IntelliSense](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![Vzdálená hlavička IntelliSense](media/connection-manager-vs2019.png)

Můžete povolit protokolování, které vám pomůžou při řešení problémů:

![Vzdálené protokolování](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Viz také:

[Nastavení vlastností kompilátoru a sestavení](../build/working-with-project-properties.md)<br/>
[C++Obecné vlastnosti (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Adresáře VC + + (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Kopírovat zdrojové vlastnosti projektu (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Vlastnosti události sestavení (Linux C++)](../linux/prop-pages/build-events-linux.md)
