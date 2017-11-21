---
title: "Konfigurace projektu C++ Linux v sadě Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e727f4588c425e3a6c94d7ceb09ebc8d494e24cf
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="configure-a-linux-project"></a>Konfigurace projektu Linux
Toto téma popisuje postup konfigurace projektu Visual Studio Linux. Informace o projektech CMake Linux najdete v tématu [konfigurace projektu CMake Linux ](cmake-linux-project.md).

## <a name="general-settings"></a>Obecná nastavení
Pro projekt Linux pomocí sady Visual Studio můžete nakonfigurovat různé možnosti.  Pokud chcete zobrazit tyto možnosti, vyberte **Projekt > vlastnosti** nabídky, nebo klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **vlastnosti** v místní nabídce. **Obecné** nastavení se zobrazí.

![Obecná konfigurace](media/settings_general.png)

Ve výchozím nastavení je spustitelný soubor (.out) vytvořené s nástroj.  K vytvoření statické nebo dynamické knihovny nebo použít existující soubor pravidel, pomocí **typ konfigurace** výběr.

## <a name="remote-settings"></a>Nastavení vzdáleného přístupu
Chcete-li změnit nastavení, která se týkají vzdáleného počítače se systémem Linux, nakonfigurujte vzdálené možnosti, které se zobrazují v **Obecné** nastavení:

* Můžete změnit cílové počítače se systémem Linux **vzdáleného počítače sestavení** položku.  To vám umožní vybrat jedno z připojení, které jste vytvořili dříve.  Pokud chcete vytvořit nový záznam, najdete [připojení vzdáleného počítače Linux](connect-to-your-remote-linux-computer.md) části.

* **Vzdáleného sestavení kořenového adresáře** Určuje, kde je projekt založený na vzdáleného počítače se systémem Linux kořenové umístění.  To bude jako výchozí **~/projects** není-li změnit.

* **Vzdáleného adresáře sestavení projektu** je, kde budou vytvořeny tento konkrétní projekt na vzdáleného počítače se systémem Linux.  To bude jako výchozí **$(RemoteRootDir)/$(ProjectName)**, který se rozbalí a adresář s názvem po aktuální projekt, v kořenovém adresáři nastavit výše.

> [!NOTE]
> Chcete-li změnit výchozí C a C++ kompilátory nebo Linkeru a Archiver používanou pro sestavení projektu, použijte odpovídající položky v **C/C++ > Obecné** části a **Linkeru > Obecné** části.  To může být nastaven na použít konkrétní verzi RSZ nebo i kompilátoru Clang, například.

## <a name="vc-directories"></a>Adresáře VC ++
Visual Studio ve výchozím nastavení, nezahrnuje žádné úrovni systému zahrnout soubory z počítače se systémem Linux.  Například v položky **/usr/zahrnují** directory nejsou k dispozici v sadě Visual Studio.  Pro úplnou [IntelliSense](/visualstudio/ide/using-intellisense) podporu, budete muset zkopírujte tyto soubory do vhodného umístění ve svém vývojovém počítači a Visual Studio přejděte do tohoto umístění.  Jednou z možností je použití spojovací bod služby (kopie Secure) ke kopírování souborů.  Ve Windows 10, můžete použít [Bash ve Windows](https://msdn.microsoft.com/commandline/wsl/about) ke spuštění spojovací bod služby.  Pro předchozí verze systému Windows, můžete použít něco jako [PSCP (PuTTY zabezpečení kopie)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Můžete zkopírovat soubory pomocí příkazu, který je podobný následujícímu:

`scp -r linux_username@remote_host:/usr/include .`

Samozřejmě, nahraďte **linux_username** a **remote_host** hodnoty výše pro co je vhodné pro vaše vlastní prostředí.

Po zkopírování souborů, použijte **adresáře VC ++** položky v okně Vlastnosti projektu říct sadě Visual Studio, kde najít zahrnout další soubory, které byly právě zkopírovali.

![Adresáře VC ++](media/settings_directories.png)

## <a name="copy-sources"></a>Kopírovat zdroje
Při vytváření, ke zdrojovým souborům na váš vývojový počítač jsou zkopírovány do počítače se systémem Linux a zkompilovat existuje.  Ve výchozím nastavení všechny zdroje v projektu sady Visual Studio se zkopírují do umístění v výše uvedené nastavení.  Však další zdroje lze také přidat do seznamu, nebo zkopírování zdroje může být vypnuto zcela, což je výchozí nastavení pro projektu souboru pravidel.

* **Zdroje pro kopírování** Určuje, jaké zdroje jsou zkopírovány do vzdáleného počítače.  Ve výchozím nastavení **@(SourcesToCopyRemotely)** výchozí nastavení pro všechny soubory zdrojového kódu v projektu, ale neobsahuje žádné soubory asset nebo prostředků, jako jsou bitové kopie.

* **Kopírovat zdroje** lze zapnout a vypnout povolení a zakázání kopírování zdrojové soubory na vzdáleném počítači.

* **Další zdroje pro kopírování** umožňuje přidat další zdrojové soubory, které budou zkopírovány do vzdáleného systému.  Můžete zadat seznam oddělený středníkem, nebo můžete použít **: =** syntaxe k zadání názvu místních a vzdálených používat:

  `C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Události sestavení
Vzhledem k tomu, že všechny kompilace se děje ve vzdáleném počítači, několik dalších událostí sestavení jsou přidané do části události sestavení v okně Vlastnosti projektu.  Jedná se o **vzdáleného události před sestavením**, **vzdáleného událost před propojením**, a **vzdáleného události po sestavení**a dojde na vzdáleném počítači před nebo po jednotlivých kroků v proces.

![Události sestavení](media/settings_buildevents.png)

## <a name="see-also"></a>Viz také
[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)  
[C++ obecné vlastnosti (Linux C++)](../linux/prop-pages/general-linux.md)  
[Adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md)  
[Kopírovat zdroje vlastnosti projektu (Linux C++)](../linux/prop-pages/copy-sources-project.md)  
[Vytvoření vlastnosti události (Linux C++)](../linux/prop-pages/build-events-linux.md)