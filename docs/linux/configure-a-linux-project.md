---
title: Konfigurace projektu C++ Linux v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: a66e2f6b6506d995859c89d9588b59056047220e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713580"
---
# <a name="configure-a-linux-project"></a>Konfigurace projektu Linux

Toto téma popisuje postup konfigurace projektu C++ Linux v sadě Visual Studio. Informace o Linuxové projekty CMake v sadě Visual Studio najdete v tématu [konfigurace projektu Linux CMake ](cmake-linux-project.md).

## <a name="general-settings"></a>Obecné nastavení

Širokou škálu možností je nakonfigurovat pro Linux projekt pomocí sady Visual Studio.  Chcete-li zobrazit tyto možnosti, vyberte **projektu > vlastnosti** nabídek nebo kliknutím pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti** v místní nabídce. **Obecné** nastavení se zobrazí.

![Obecná konfigurace](media/settings_general.png)

Ve výchozím nastavení je spustitelný soubor (.out) vytvořené nástrojem.  Vytvoří statickou nebo dynamickou knihovnu, nebo použít existující soubor pravidel, použijte **typ konfigurace** výběru.

## <a name="remote-settings"></a>Nastavení vzdáleného přístupu

Chcete-li změnit nastavení vztahující se ke vzdálenému počítači Linux, nakonfigurujte vzdálené možnosti, které se zobrazují v **Obecné** nastavení:

- Chcete-li změnit cílový počítač s Linuxem, použijte **vzdálený počítač sestavení** položka.  To vám umožní vybrat jedno z připojení, které jste předtím vytvořili.  Chcete-li vytvořit nový záznam, přejděte prosím sem [připojení vzdáleného počítače Linux](connect-to-your-remote-linux-computer.md) části.

- **Vzdálený kořenový adresář sestavení** Určuje, kde sestavení projektu ve vzdáleném počítači Linux umístění kořenového adresáře.  To bude ve výchozím nastavení **~/projects** není-li změnit.

- **Vzdálený adresář projektu sestavení** je, kde bude vytvořen tohoto konkrétního projektu na vzdáleném počítači s Linuxem.  To bude ve výchozím nastavení **$(RemoteRootDir)/$(ProjectName)**, který se rozbalí a adresář s názvem po aktuální projekt pod kořenovým adresářem uvedené výše.

> [!NOTE]
> Ke změně výchozího jazyka C a kompilátory C++, nebo Linkeru a archivačního programu sloužící k sestavení projektu, použijte odpovídající položky v **C/C++ > Obecné** oddílu a **Linker > Obecné** oddílu.  To může být nastaven na použití určité verze GCC, nebo dokonce kompilátoru Clang, třeba.

## <a name="include-directories-and-intellisense-support"></a>Zahrnout adresáře a podporu technologie IntelliSense

**Visual Studio 2017 verze 15.6 a starší:**<br/>
Ve výchozím nastavení Visual Studio nezahrnuje všech souborů include úrovni systému z počítače s Linuxem.  Příklad položky v **/usr/include** adresáře nejsou k dispozici v sadě Visual Studio.
Úplné [IntelliSense](/visualstudio/ide/using-intellisense) podpory, budete muset zkopírovat tyto soubory do umístění ve svém vývojovém počítači a sady Visual Studio přejděte do tohoto umístění.  Jednou z možností je použití spojovacího bodu služby (Secure Copy) ke kopírování souborů.  Ve Windows 10, můžete použít [Bash ve Windows](https://msdn.microsoft.com/commandline/wsl/about) ke spuštění spojovací bod služby.  U předchozích verzí systému Windows, například použít něco jako [PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Zkopírujte soubory s použitím příkazu, který je podobný následujícímu:

`scp -r linux_username@remote_host:/usr/include .`

Samozřejmě, nahraďte **linux_username** a **remote_host** hodnoty vyšší než co je vhodné pro vaše vlastní prostředí.

Po zkopírování souborů, použijte **adresáře VC ++** položky ve vlastnostech projektu sady Visual Studio zjistit, kde najdete další vložené soubory, které byly zkopírovány pouze.

![Adresáře VC ++](media/settings_directories.png)

**Visual Studio 2017 verze 15.7 nebo novější:**<br/>
Zobrazit [Správa vzdálených hlaviček IntelliSense](#remote_intellisense).

## <a name="copy-sources"></a>Kopírovat zdroje

Při sestavování, jsou zdrojové soubory na vašem počítači zkopírují do počítače s Linuxem a zkompilovány existuje.  Ve výchozím nastavení všechny zdroje v projektu sady Visual Studio se zkopírují do umístění v nastavení výše.  Však další zdroje můžete také přidat do seznamu nebo kopírování zdrojů může být vypnuto úplně, což je výchozí nastavení pro projektu souboru pravidel.

- **Zdroje ke zkopírování** Určuje, jaké zdroje jsou zkopírovány do vzdáleného počítače.  Ve výchozím nastavení  **\@(SourcesToCopyRemotely)** ve výchozím nastavení všechny soubory zdrojového kódu v projektu, ale neobsahuje žádné soubory prostředků nebo prostředek, jako jsou obrázky.

- **Kopírovat zdroje** lze zapnout a vypnout můžete povolit nebo zakázat kopírování zdrojových souborů do vzdáleného počítače.

- **Další zdroje ke zkopírování** vám umožní přidávat další zdrojové soubory, které budou zkopírovány do vzdáleného systému.  Středníkem oddělený seznam můžete zadat, nebo můžete použít **: =** syntaxe pro určení názvu místních a vzdálených používat:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Události sestavení

Protože všechny kompilace se děje ve vzdáleném počítači, několik dalších události sestavení se přidaly do části události sestavení ve vlastnostech projektu.  Jedná se o **Vzdálená událost před sestavením**, **Vzdálená událost před propojením**, a **Vzdálená událost po sestavení**a dojde na vzdáleném počítači před nebo po jednotlivých krocích proces.

![Události sestavení](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> Technologie IntelliSense pro vzdálených hlaviček (Visual Studio 2017 verze 15.7 nebo novější)

Při přidání nového připojení v **Správce připojení**, sada Visual Studio automaticky zjistí adresáře vložených souborů pro kompilátor ve vzdáleném systému. Visual Studio pak zips a zkopíruje soubory do adresáře na místním počítači Windows. Potom při každém použití připojení v sadě Visual Studio nebo CMake projektu, se záhlaví v těchto adresářích používají k zajištění technologie IntelliSense.

Tato funkce závisí na počítači s Linuxem s zip nainstalované. Zip můžete nainstalovat pomocí tohoto příkazu apt-get:

```cmd
apt install zip
```

Ke správě vaší mezipaměti hlaviček, přejděte na **nástroje > Možnosti, různé platformy > Správce připojení > vzdáleného správce IntelliSense záhlaví**. Aktualizace hlaviček mezipaměti po provedení změny na počítač s Linuxem, vyberte vzdáleného připojení a pak vyberte **aktualizovat**. Vyberte **odstranit** odebrat záhlaví bez odstranění samotného připojení. Vyberte **prozkoumat** otevření místní adresáře v **Průzkumníka souborů**. Tato složka považovat jen pro čtení. Chcete-li stáhnout hlavičky pro existující připojení, který byl vytvořen starší než verze 15.3, vyberte připojit a pak vyberte **Stáhnout**.

![Vzdálené hlaviček IntelliSense](media/remote-header-intellisense.png)

## <a name="see-also"></a>Viz také

[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)  
[C++ obecné vlastnosti (Linux C++)](../linux/prop-pages/general-linux.md)  
[Adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md)  
[Kopírovat projekt vlastností zdrojů (Linux C++)](../linux/prop-pages/copy-sources-project.md)  
[Vytvořit událost vlastnosti (Linux C++)](../linux/prop-pages/build-events-linux.md)