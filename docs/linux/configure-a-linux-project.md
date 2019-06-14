---
title: Konfigurace projektu C++ Linux v sadě Visual Studio
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: a4e20222cc0b04f496989bf2d51fc12c85f5d162
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042632"
---
# <a name="configure-a-linux-project"></a>Konfigurace projektu Linux

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

Toto téma popisuje postup konfigurace C++ projektu Linux, jak je popsáno v [vytvořte nový C++ projektu Linux v sadě Visual Studio](create-a-new-linux-project.md). CMake Linuxových projektů, naleznete v tématu [konfigurace projektu Linux CMake ](cmake-linux-project.md). 

Můžete konfigurace projektu Linux cílit na fyzický počítač s Linuxem, virtuálních počítačů nebo [subsystém Windows pro Linux](/windows/wsl/about) (WSL). 

::: moniker range="vs-2019"

**Visual Studio 2019 version 16.1**:

- Při cílení na WSL, můžete se vyhnout kopírování operace, které jsou nezbytné k vytváření, technologie IntelliSense při cílení na vzdálených Linuxových systémů.

- Můžete zadat samostatnou Linuxových cílů pro sestavování a ladění.

::: moniker-end

## <a name="general-settings"></a>Obecná nastavení

Chcete-li zobrazit možnosti konfigurace, vyberte **projektu > vlastnosti** nabídek nebo kliknutím pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti** z kontextu nabídka. **Obecné** nastavení se zobrazí.

![Obecná konfigurace](media/settings_general.png)

Ve výchozím nastavení je sestaven spustitelný soubor (.out). Vytvoří statickou nebo dynamickou knihovnu, nebo použít existující soubor pravidel, použijte **typ konfigurace** nastavení.

Další informace o nastavení na stránkách vlastností najdete v tématu [odkaz na stránku vlastností projektu Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Nastavení vzdáleného přístupu

Chcete-li změnit nastavení vztahující se na vzdálené počítače s Linuxem, konfigurace, které se zobrazí v části Nastavení vzdáleného [Obecné](prop-pages/general-linux.md).

- Pokud chcete zadat vzdálený cílový počítač Linux, použijte **vzdálený počítač sestavení** položka. To vám umožní vybrat jedno z připojení, které jste předtím vytvořili. Pokud chcete vytvořit nový záznam, najdete v článku [připojení vzdáleného počítače Linux](connect-to-your-remote-linux-computer.md) části.

   ![Sestavení počítače](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 version 16.1**: Zacílené subsystém Windows pro Linux, klikněte na šipku dolů u **sada nástrojů platformy** a zvolte **WSL_1_0**. Další možnosti vzdáleného zmizí a zobrazí se místo nich cestu k výchozí WSL prostředí:

   ![WSL sestavující počítač](media/wsl-remote-vs2019.png)

   Pokud máte zařízení WSL vedle sebe, můžete zadat jinou cestu. Další informace o správě více distribucích najdete v tématu [spravovat a konfigurovat subsystém Windows pro Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Můžete určit jiný cíl pro ladění na **vlastnosti konfigurace** > **ladění** stránky.

   ::: moniker-end

- **Vzdálený kořenový adresář sestavení** Určuje, kde sestavení projektu ve vzdáleném počítači Linux umístění kořenového adresáře. To bude ve výchozím nastavení **~/projects** není-li změnit.

- **Vzdálený adresář projektu sestavení** je, kde bude vytvořen tohoto konkrétního projektu na vzdáleném počítači s Linuxem. To bude ve výchozím nastavení **$(RemoteRootDir)/$(ProjectName)** , který se rozbalí a adresář s názvem po aktuální projekt pod kořenovým adresářem uvedené výše.

> [!NOTE]
> Ke změně výchozího jazyka C a kompilátory C++, nebo Linkeru a archivačního programu sloužící k sestavení projektu, použijte odpovídající položky v **C/C++ > Obecné** oddílu a **Linker > Obecné** oddílu. Můžete třeba zadat určité verzi GCC nebo Clang. Další informace najdete v části [vlastnosti C/C++ (Linux C++)](prop-pages/c-cpp-linux.md) a [vlastnosti Linkeru (Linux C++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Kopírovat zdroje (pouze pro vzdálené systémy)

::: moniker range="vs-2019"

Tato část se nevztahuje při cílení na WSL.

::: moniker-end

Při sestavování ve vzdálených systémech, jsou zdrojové soubory na vašem počítači zkopírují do počítače s Linuxem a zkompilovány existuje. Ve výchozím nastavení všechny zdroje v projektu sady Visual Studio se zkopírují do umístění v nastavení výše. Však další zdroje můžete také přidat do seznamu nebo kopírování zdrojů může být vypnuto úplně, což je výchozí nastavení pro projektu souboru pravidel.

- **Zdroje ke zkopírování** Určuje, jaké zdroje jsou zkopírovány do vzdáleného počítače. Ve výchozím nastavení  **\@(SourcesToCopyRemotely)** ve výchozím nastavení všechny soubory zdrojového kódu v projektu, ale neobsahuje žádné soubory prostředků nebo prostředek, jako jsou obrázky.

- **Kopírovat zdroje** lze zapnout a vypnout můžete povolit nebo zakázat kopírování zdrojových souborů do vzdáleného počítače.

- **Další zdroje ke zkopírování** vám umožní přidávat další zdrojové soubory, které budou zkopírovány do vzdáleného systému. Středníkem oddělený seznam můžete zadat, nebo můžete použít **: =** syntaxe pro určení názvu místních a vzdálených používat:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Události sestavení

Protože všechny kompilace probíhá na vzdáleném počítači (nebo WSL), několik dalších události sestavení se přidaly do části události sestavení ve vlastnostech projektu. Jedná se o **Vzdálená událost před sestavením**, **Vzdálená událost před propojením**, a **Vzdálená událost po sestavení**a dojde na vzdáleném počítači před nebo po jednotlivých krocích proces.

![Události sestavení](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> Technologie IntelliSense pro záhlaví ve vzdálených systémech

::: moniker range="vs-2019"

Tato část se nevztahuje při cílení na WSL.

::: moniker-end

Při přidání nového připojení v **Správce připojení**, sada Visual Studio automaticky zjistí adresáře vložených souborů pro kompilátor ve vzdáleném systému. Visual Studio pak zips a zkopíruje soubory do adresáře na místním počítači Windows. Potom při každém použití připojení v sadě Visual Studio nebo CMake projektu, se záhlaví v těchto adresářích používají k zajištění technologie IntelliSense.

Tato funkce závisí na počítači s Linuxem s zip nainstalované. Zip můžete nainstalovat pomocí tohoto příkazu apt-get:

```cmd
sudo apt install zip
```

Ke správě vaší mezipaměti hlaviček, přejděte na **nástroje > Možnosti, různé platformy > Správce připojení > vzdáleného správce IntelliSense záhlaví**. Aktualizace hlaviček mezipaměti po provedení změny na počítač s Linuxem, vyberte vzdáleného připojení a pak vyberte **aktualizovat**. Vyberte **odstranit** odebrat záhlaví bez odstranění samotného připojení. Vyberte **prozkoumat** otevření místní adresáře v **Průzkumníka souborů**. Tato složka považovat jen pro čtení. Chcete-li stahovat hlavičky pro existující připojení, který byl vytvořen před Visual Studio 2017 verze 15.3, vyberte požadované připojení a pak vyberte **Stáhnout**.

::: moniker range="vs-2017"

![Vzdálené hlaviček IntelliSense](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![Vzdálené hlaviček IntelliSense](media/connection-manager-vs2019.png)

Můžete povolit protokolování, které vám pomohou vyřešit problémy:

![Vzdálené přihlášení](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Viz také:

[Nastavení kompilátoru a vlastnosti sestavení](../build/working-with-project-properties.md)<br/>
[C++ obecné vlastnosti (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Kopírovat projekt vlastností zdrojů (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Vytvořit událost vlastnosti (Linux C++)](../linux/prop-pages/build-events-linux.md)
