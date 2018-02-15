---
title: "Obecná stránka vlastností (projekt) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 772192a4b367760e85bb1631f1ef7b50650af0c1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="general-property-page-project"></a>Obecná stránka vlastností (projekt)

Když na uzel projektu v v Průzkumníku řešení klikněte pravým tlačítkem a vyberete **vlastnosti**, **Obecné** stránka vlastností v rámci **vlastnosti konfigurace** uzlu Levý panel zobrazuje dva oddíly vlastností:

- Obecné

- Výchozí nastavení projektu

Projekty jiný systém než Windows, najdete v části [odkazu na stránku vlastností C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="general"></a>Obecné

Vlastnosti v části Obecné ovlivňují umístění souborů, které jsou vytvořené v procesu sestavení a které soubory jsou při odstranění **Vyčistit** možnost (**sestavení** nabídky) je vybrána.

Cílová platforma  
Určuje platformy, na které projekt se spustí na. Například Windows, Android nebo iOS. Hodnota **Windows 10** znamená cíle projektu univerzální platformu Windows. Pokud cílíte na starších verzích systému Windows, verze není uvedena a hodnotu v tomto poli se zobrazí jako jenom **Windows**. Toto je jen pro čtení pole, který je nastavený při vytváření projektu.

**Verze sady SDK pro Windows**  
Pro cílové platformy Windows určuje verzi sady Windows SDK, který vyžaduje projekt. Když instalujete zatížení C++ pomocí instalačního programu sady Visual Studio, jsou nainstalovány také části požadované sady Windows SDK. Pokud máte další verze sady Windows SDK na váš počítač, zobrazí se v rozevírací nabídce každou verzi sady SDK nástroje, které jste nainstalovali.

Pokud chcete zacílit, Windows 7 nebo Windows Vista, použijte hodnotu **8.1**, protože Windows SDK 8.1 je zpětně kompatibilní, aby tyto platformy. Kromě toho byste měli definovat hodnotu vhodnou pro **_WIN32_WINNT** v targetver.h. Pro systém Windows 7, který je 0x0601. V tématu [úpravy maker WINVER a _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

Sada nástrojů platformy systému Windows XP, zahrnuté v sadě Visual Studio na použití aktuální verze knihoven k vytvoření projektů, Windows XP a Windows 2003 Server můžete nainstalovat. Informace o tom, jak získat a použít tato sada nástrojů platformy najdete v tématu [konfigurace programů pro systém Windows XP](../build/configuring-programs-for-windows-xp.md). Další informace o změně sada nástrojů platformy najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

**Cílové platformy Min. Verze**  
Určuje nejnižší verze platformy, na které můžete spustit projekt na. Tato vlastnost se zobrazí jenom v případě, že typ projektu podporuje, například v projektech univerzální pro Windows. Pokud vaše aplikace mohou využít výhod funkcí v novější verzi sady Windows SDK, ale pořád dá spustit v dřívějších verzích bez těchto funkcí, třeba s ztrátě některých funkcí, pak hodnota tyto dvě vlastnosti může lišit. Pokud ano, by měl váš kód zkontrolujte verzi platformy je spuštěn s za běhu a není snaží používat funkce, které nejsou k dispozici ve starší verzi platformy.

Všimněte si, že Visual C++ nevynucuje tuto možnost. Je zahrnuté pro konzistence s jinými jazyky, jako je například C# a JavaScript a jako vodítko pro každého, kdo používá váš projekt. Visual C++ nevygeneruje chybu, pokud používáte funkci, která není k dispozici v minimální verzi.

Výstupní adresář  
Určuje adresář, kde nástroje, jako je linkeru umístí všechny soubory závěrečný výstup, které jsou vytvořené během procesu vytváření. Obvykle obsahuje výstup nástroje, například linkeru, librarian nebo BSCMake. Ve výchozím nastavení, tato vlastnost je adresář zadaný $ $(SolutionDir) makra (konfigurace) \.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

Zprostředkující adresáře  
Určuje adresář, kde nástroje, jako je kompilátor umístí všechny zprostředkující soubory vytvořené během procesu sestavení. Obvykle obsahuje výstup nástroje, jako je kompilátor C/C++, MIDL a kompilátor prostředků. Ve výchozím nastavení, tato vlastnost je adresář zadaný makro $(konfigurace) \.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

**Název cíle**  
Určuje název souboru, který generuje tento projekt. Ve výchozím nastavení tato vlastnost je název souboru určeného makro $(ProjectName).

Přípona cílového  
Určuje příponu názvu souboru, který tento projekt generuje; například .exe nebo .dll.

Rozšíření k odstranění na vyčištění  
**Vyčistit** možnost (**sestavení** nabídky) odstraní soubory z mezilehlého adresáře, ve kterém je sestavena konfigurace projektu. Soubory s příponami zadaný s touto vlastností bude odstraněn, když **Vyčistit** nebo při opětovném sestavení. Kromě souborů v adresáři zprostředkující tato rozšíření systém sestavení také odstraní všechny známé výstupy sestavení bez ohledu na to, kde se nachází (včetně mezilehlých výstupů, jako jsou například soubory .obj). Všimněte si, že je možné zadat zástupné znaky.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

Vytvoření souboru protokolu  
Umožňuje určit jiné než výchozí umístění souboru protokolu, který se vytvoří vždy, když vytváříte projekt. Výchozí umístění je určena .log makra $(IntDir) $(MSBuildProjectName).

Chcete-li změnit umístění adresáře můžete makra projektu. V tématu [běžné makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md).

Sada nástrojů platformy  
Umožňuje projekt, který má jinou verzi knihovny jazyka Visual C++ a kompilátoru. Projekty Visual C++, můžete vybrat nástrojů výchozí nainstalované sady Visual Studio nebo jeden z modulové nainstalovat pomocí několika dřívějších verzí sady Visual Studio, včetně modulové, vytvoříte spustitelné soubory, které můžete spustit na Windowx XP. Informace o změně sada nástrojů platformy najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

**Povolit spravované přírůstkové sestavení**  
Pro spravované projekty umožňuje detekovat externí viditelnosti, při generování sestavení. Pokud není viditelná pro další projekty ke změně spravovaný projekt, pak závislé projekty nejsou znovu sestavit. To může výrazně zlepšit časy sestavení v řešení, které obsahují spravované projekty.

## <a name="project-defaults"></a>Výchozí nastavení projektu

Vlastnosti v části výchozí projekt představují výchozí vlastnosti, které lze upravit. Definice těchto vlastností najdete v souborech v *instalační adresář*\VC\VCProjectDefaults.

Typ konfigurace  
Existuje několik typů konfiguraci pro výběr:

- **Aplikace (.exe)**, zobrazí linkeru nástrojů (kompilátor C/C++, MIDL, kompilátor prostředků, Linkeru, BSCMake, Generátor XML webové služby serveru proxy serveru, vlastní sestavení, události prebuild, prelink, konfiguraci událostí).

- **Dynamická knihovna (DLL)**, zobrazí linkeru sadu nástrojů, určuje/DLL – možnost linkeru a přidá _WINDLL zadat CL.

- **Makefile**, zobrazí sadu nástrojů makefile (NMake).

- **Statické knihovny (LIB)**, zobrazí sadu nástrojů librarian (stejný jako linkeru nástrojů s výjimkou nahraďte librarian linkeru a vynechat možnost Generátor XML webové služby serveru proxy serveru).

- **Nástroj**, zobrazí sadu nástrojů nástroje (MIDL, vlastní sestavení, události prebuild, postbuild).

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

**Použití knihovny MFC**  
Určuje, zda v projektu knihovny MFC staticky nebo dynamicky odkaz ke knihovně MFC DLL. Můžete vybrat projekty bez knihovny MFC **použít standardní knihovny Windows** propojení s různými knihovnami Win32, které jsou zahrnuty při použití knihovny MFC.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

**Použití knihovny ATL**  
Určuje, zda projekt knihovny ATL staticky nebo dynamicky odkaz ATL. KNIHOVNY DLL. Pokud zadáte cokoli jiné než **není pomocí knihovny ATL**, definujte se zařadí do kompilátoru **příkazového řádku** stránka vlastností.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>.

Znakové sady  
Definuje, zda _UNICODE nebo _MBCS musí být nastavená. Také ovlivní linkeru vstupního bodu, kde je to vhodné.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

**Podpora Common Language Runtime**  
Způsobí, že [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru má být použit.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

**Verze rozhraní .NET Framework cíl**  
Ve spravovaných projekty určuje verze rozhraní .NET framework k cíli.

**Optimalizace celého programu**  
Určuje, [/GL](../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru a [/ltgc](../build/reference/ltcg-link-time-code-generation.md) – možnost linkeru. Ve výchozím nastavení to je zakázán pro konfiguraci ladění a povolený pro maloobchodní konfigurace.

**Podpora aplikací pro Windows Store**  
Určuje, jestli podporuje tento projekt aplikace Windows Runtime (Universal Windows Platform). Další informace najdete v tématu [/ZW (kompilace Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md)a Centrum vývojářů pro Windows.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../ide/property-pages-visual-cpp.md)  