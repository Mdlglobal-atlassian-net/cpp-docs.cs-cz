---
title: Obecná stránka vlastností (projekt)
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: eb172e7bd76816458a0efff7b053d136f52076ab
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166755"
---
# <a name="general-property-page-project"></a>Obecná stránka vlastností (projekt)

::: moniker range=">=vs-2019"

Toto téma se vztahuje na projekty sady Visual Studio pro systém Windows. Pro projekty pro Linux se podívejte na [odkaz na stránku vlastností Linux C++ ](../../linux/prop-pages-linux.md). Projekty CMake najdete v tématu [projekty cmake v sadě Visual Studio](../cmake-projects-in-visual-studio.md). Projekty pro Android najdete v tématu [Obecné vlastnosti projektu ( C++Android)](/cpp/cross-platform/general-android-prop-page). Projekty souborů pravidel Androidu naleznete v tématu [Obecné vlastnosti projektu C++ (soubor pravidel Androidu)](/cpp/cross-platform/general-makefile-android-prop-page) .

Když kliknete pravým tlačítkem myši na uzel projektu v Průzkumník řešení a vyberete **vlastnosti**, stránka **Obecné** vlastnosti pod uzlem **Vlastnosti konfigurace** v levém podokně zobrazí tyto vlastnosti:

- **Výstupní adresář**

   Určuje adresář, do kterého nástroje, jako je třeba linker, umístí všechny finální výstupní soubory, které jsou vytvořeny během procesu sestavení. Obvykle to zahrnuje výstup nástrojů, jako je linker, librarian nebo BSCMake. Ve výchozím nastavení je tato vlastnost adresářem určeným makry $ (SolutionDir) $ (konfigurace) \.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Zprostředkující adresář**

   Určuje adresář, do kterého nástroje, jako je třeba kompilátor, umístí všechny mezilehlé soubory vytvořené během procesu sestavení. Obvykle to zahrnuje výstup nástrojů, jako je C/C++ COMPILER, MIDL a kompilátor prostředků. Ve výchozím nastavení je tato vlastnost adresářem určeným makrem $ (konfigurace) \.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Název cíle**

   Určuje název souboru, který tento projekt vygeneruje. Ve výchozím nastavení je tato vlastnost název souboru zadaný pomocí makra $ (ProjectName).

- **Typ konfigurace**

  Existuje několik typů konfigurace, ze kterých si můžete vybrat:

  - **Aplikace (. exe)**

     Zobrazí sadu nástrojů linkeru (C++ C/COMPILER, MIDL, kompilátor prostředků, linker, BSCMAKE, generátor proxy webové služby XML, vlastní sestavení, představování, předpojování, události postbuild).

  - **Dynamická knihovna (. dll)**

     Zobrazí sadu nástrojů linkeru, Určuje možnost linkeru/DLL a přidá _WINDLL definováno pro CL.

  - **Makefile**

     Zobrazí sadu nástrojů makefile (NMake).

  - **Statická knihovna (. lib)**

     Zobrazí sadu nástrojů Librarian (stejně jako sadu nástrojů linkeru s výjimkou náhradních Librarian pro Linker a vynechání generátoru proxy webové služby XML).

  - **Spuštění**

     Zobrazí sadu nástrojů nástrojů (MIDL, vlastní sestavení, představování a postbuild události).

  Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Verze Windows SDK**

   Pro cílovou platformu Windows určuje verzi Windows SDK, kterou váš projekt vyžaduje. Když nainstalujete C++ úlohu pomocí instalačního programu sady Visual Studio, nainstalují se taky požadované části Windows SDK. Pokud máte v počítači jiné verze Windows SDK, v rozevíracím seznamu se zobrazí každá verze nástrojů sady SDK, které jste nainstalovali.

   Chcete-li cílit na systém Windows 7 nebo Windows Vista, použijte hodnotu **8,1**, protože Windows SDK 8,1 je zpětně kompatibilní s těmito platformami. Kromě toho byste měli definovat vhodnou hodnotu pro **_WIN32_WINNT** v targetver. h. Pro Windows 7 to je 0x0601. Viz [Úpravy winver a _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Sadu nástrojů platformy Windows XP, která je součástí sady Visual Studio, můžete nainstalovat tak, aby používala aktuální verzi knihoven k sestavování projektů Windows XP a Windows 2003 serveru. Informace o tom, jak získat a použít tuto sadu nástrojů platformy, najdete v tématu [Konfigurace programů pro systém Windows XP](../configuring-programs-for-windows-xp.md). Další informace o změně sady nástrojů platformy naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Sada nástrojů platformy**

   Umožňuje projektu cílit na jinou verzi knihoven a kompilátorů vizuálů C++ . Projekty sady C++ Visual Studio mohou cílit buď na výchozí sadu nástrojů nainstalovanou sadou Visual Studio, nebo na jednu ze sad nástrojů nainstalovaných několika předchozími verzemi sady Visual Studio, včetně sad nástrojů pro vytváření spustitelných souborů, které lze spustit v systému Windows XP. Informace o změně sady nástrojů platformy naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **C++Standardní jazyk**

   Určuje jazykovou normu, která se má použít. Výchozí hodnota je/std: c++ 14. Zadejte/std: c++ 17 pro použití funkcí C++ 17 nebo/std: c++ + nejnovější pro použití C++ 20 nebo dalších experimentálních funkcí. Další informace najdete v tématu [/std (zadání jazykové verze Standard)](std-specify-language-standard-version.md) .

::: moniker-end

::: moniker range="<=vs-2017"

Pokud v aplikaci Visual Studio 2015 a Visual Studio 2017 kliknete pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**a vyberete možnost **vlastnosti**, zobrazí se na stránce vlastností **Obecné** v uzlu **Vlastnosti konfigurace** v levém podokně dvě části vlastností:

- Obecné

- Výchozí nastavení projektu

## <a name="general"></a>Obecné

- **Cílová platforma**

   Určuje platformu, na které bude projekt běžet. Například Windows, Android nebo iOS. Hodnota **Windows 10** znamená, že projekt cílí na Univerzální platforma Windows. Pokud cílíte na starší verze Windows, verze není v seznamu a hodnota v tomto poli se zobrazí jako jenom **Windows**. Toto je pole jen pro čtení, které je nastaveno při vytváření projektu.

- **Verze cílové platformy (Visual Studio 2015)**

   Určuje nejnižší verzi platformy, na které může projekt běžet. Tato vlastnost se zobrazí pouze v případě, že je typ projektu podporuje. Pokud vaše aplikace může využít výhod funkcí v novější verzi Windows SDK, ale může běžet i v dřívějších verzích bez těchto funkcí, třeba s určitou ztrátou funkčnosti, pak se hodnota těchto dvou vlastností může lišit. Pokud ano, váš kód by měl kontrolovat verzi platformy, na které běží, za běhu a nepokusit se používat funkce, které nejsou dostupné ve starší verzi platformy.

   Systém C++ projektu tuto možnost nevynutil. Je součástí konzistence s jinými jazyky, jako jsou C# například a JavaScript, a jako vodítko pro kohokoli, kdo používá váš projekt. Pokud C++ použijete funkci, která není k dispozici v minimální verzi, vizuál negeneruje chybu.

- **Verze Windows SDK (Visual Studio 2017)**

   Pro cílovou platformu Windows určuje verzi Windows SDK, kterou váš projekt vyžaduje. Když nainstalujete C++ úlohu pomocí instalačního programu sady Visual Studio, nainstalují se taky požadované části Windows SDK. Pokud máte v počítači jiné verze Windows SDK, v rozevíracím seznamu se zobrazí každá verze nástrojů sady SDK, které jste nainstalovali.

   Chcete-li cílit na systém Windows 7 nebo Windows Vista, použijte hodnotu **8,1**, protože Windows SDK 8,1 je zpětně kompatibilní s těmito platformami. Kromě toho byste měli definovat vhodnou hodnotu pro **_WIN32_WINNT** v targetver. h. Pro Windows 7 to je 0x0601. Viz [Úpravy winver a _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Sadu nástrojů platformy Windows XP, která je součástí sady Visual Studio, můžete nainstalovat tak, aby používala aktuální verzi knihoven k sestavování projektů Windows XP a Windows 2003 serveru. Informace o tom, jak získat a použít tuto sadu nástrojů platformy, najdete v tématu [Konfigurace programů pro systém Windows XP](../configuring-programs-for-windows-xp.md). Další informace o změně sady nástrojů platformy naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Výstupní adresář**

   Určuje adresář, do kterého nástroje, jako je třeba linker, umístí všechny finální výstupní soubory, které jsou vytvořeny během procesu sestavení. Obvykle to zahrnuje výstup nástrojů, jako je linker, librarian nebo BSCMake. Ve výchozím nastavení je tato vlastnost adresářem určeným makry $ (SolutionDir) $ (konfigurace) \.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Zprostředkující adresář**

   Určuje adresář, do kterého nástroje, jako je třeba kompilátor, umístí všechny mezilehlé soubory vytvořené během procesu sestavení. Obvykle to zahrnuje výstup nástrojů, jako je C/C++ COMPILER, MIDL a kompilátor prostředků. Ve výchozím nastavení je tato vlastnost adresářem určeným makrem $ (konfigurace) \.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Název cíle**

   Určuje název souboru, který tento projekt vygeneruje. Ve výchozím nastavení je tato vlastnost název souboru zadaný pomocí makra $ (ProjectName).

- **Cílová Přípona**

   Určuje příponu názvu souboru, který tento projekt vygeneruje. například. exe nebo. dll.

- **Přípony k odstranění při čištění**

   Možnost **vyčistit** (nabídka**sestavení** ) odstraní soubory z mezilehlého adresáře, kde je vytvořena konfigurace projektu. Soubory s příponami, které jsou zadané pomocí této vlastnosti, se odstraní, když se spustí **Vyčištění** nebo když provedete opětovné sestavení. Kromě souborů těchto rozšíření v zprostředkujícím adresáři systém sestavení také odstraní jakýkoliv známý výstup sestavení bez ohledu na to, kde se nachází (včetně mezilehlých výstupů, jako jsou soubory. obj). Všimněte si, že můžete zadat zástupné znaky.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Soubor protokolu sestavení**

   Umožňuje zadat jiné než výchozí umístění souboru protokolu, který se vytvoří při každém sestavení projektu. Výchozí umístění je zadáno pomocí makra $ (IntDir) $ (MSBuildProjectName) $ (). log.

   Můžete použít makra projektu ke změně umístění adresáře. Viz [společná makra pro příkazy a vlastnosti buildu](common-macros-for-build-commands-and-properties.md).

- **Sada nástrojů platformy**

   Umožňuje projektu cílit na jinou verzi knihoven a kompilátorů vizuálů C++ . Projekty sady C++ Visual Studio mohou cílit buď na výchozí sadu nástrojů nainstalovanou sadou Visual Studio, nebo na jednu ze sad nástrojů nainstalovaných několika předchozími verzemi sady Visual Studio, včetně sad nástrojů pro vytváření spustitelných souborů, které lze spustit v systému Windows XP. Informace o změně sady nástrojů platformy naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Povolit spravované přírůstkové sestavení**

   U spravovaných projektů to umožňuje detekci externí viditelnosti při generování sestavení. Pokud změna spravovaného projektu není viditelná pro jiné projekty, pak nejsou znovu sestaveny závislé projekty. To může výrazně zlepšit dobu sestavení v řešeních, která zahrnují spravované projekty.

## <a name="project-defaults"></a>Výchozí nastavení projektu

Vlastnosti ve výchozím oddílu projektu reprezentují výchozí vlastnosti, které lze upravit. Definici pro tyto vlastnosti lze nalézt v souborech. props v *instalačním adresáři*\VC\VCProjectDefaults.

- **Typ konfigurace**

  Existuje několik typů konfigurace, ze kterých si můžete vybrat:

  - **Aplikace (. exe)**

     Zobrazí sadu nástrojů linkeru (C++ C/COMPILER, MIDL, kompilátor prostředků, linker, BSCMAKE, generátor proxy webové služby XML, vlastní sestavení, představování, předpojování, události postbuild).

  - **Dynamická knihovna (. dll)**

     Zobrazí sadu nástrojů linkeru, Určuje možnost linkeru/DLL a přidá _WINDLL definováno pro CL.

  - **Makefile**

     Zobrazí sadu nástrojů makefile (NMake).

  - **Statická knihovna (. lib)**

     Zobrazí sadu nástrojů Librarian (stejně jako sadu nástrojů linkeru s výjimkou náhradních Librarian pro Linker a vynechání generátoru proxy webové služby XML).

  - **Spuštění**

     Zobrazí sadu nástrojů nástrojů (MIDL, vlastní sestavení, představování a postbuild události).

  Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Použití knihovny MFC**

   Určuje, zda projekt knihovny MFC bude staticky nebo dynamicky propojen s knihovnou MFC DLL. Projekty mimo knihovnu MFC mohou vybrat možnost **použít standardní knihovny Windows** pro propojení s různými knihovnami Win32, které jsou zahrnuty při použití knihovny MFC.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Znaková sada**

   Definuje, zda by měla být nastavena _UNICODE nebo _MBCS. Také ovlivňuje vstupní bod linkeru, kde je to vhodné.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Podpora modulu CLR (Common Language Runtime)**

   Způsobí použití možnosti kompilátoru [/CLR](clr-common-language-runtime-compilation.md) .

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Cílová verze rozhraní .NET Framework**

   Ve spravovaných projektech určuje cílovou verzi rozhraní .NET Framework.

- **Optimalizace celého programu**

   Určuje možnost kompilátoru [/GL](gl-whole-program-optimization.md) a možnost linkeru [/LTCG](ltcg-link-time-code-generation.md) . Ve výchozím nastavení je tato možnost zakázána pro konfiguraci ladění a je povolena pro maloobchodní konfigurace.

- **Podpora aplikací pro Windows Store**

   Určuje, jestli tento projekt podporuje aplikace prostředí Windows Runtime (Univerzální platforma Windows). Další informace naleznete v tématu [/ZW (prostředí Windows Runtime Compilation)](zw-windows-runtime-compilation.md)a ve středisku pro vývojáře v systému Windows.

::: moniker-end

## <a name="see-also"></a>Viz také

[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)
