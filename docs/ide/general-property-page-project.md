---
title: Obecná stránka vlastností (projekt) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
ms.workload:
- cplusplus
ms.openlocfilehash: 4d68cf6be3a512d478f4d7808ce321f18c0efd84
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422250"
---
# <a name="general-property-page-project"></a>Obecná stránka vlastností (projekt)

Když pravým tlačítkem myši na uzel projektu v Průzkumníku řešení a vyberete **vlastnosti**, **Obecné** stránka vlastností **vlastnosti konfigurace** uzlu v levém podokně zobrazí dva oddíly vlastností:

- Obecné

- Výchozí vlastnosti projektu

Projekty bez Windows, naleznete v tématu [odkaz na stránku vlastností Linux C++](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="general"></a>Obecné

Vlastnosti v oddíle Obecná ovlivňují umístění souborů, které jsou vytvořeny během procesu sestavení a které soubory jsou odstraněny při **Vyčistit** možnost (**sestavení** nabídky) je vybraná.

- **Cílová platforma**

   Určuje, který se spustí projekt na platformu. Například Windows, Android nebo iOS. Hodnota **Windows 10** znamená, že je projekt zaměřen univerzální platformu Windows. Pokud cílíte na starších verzích Windows, není uvedená verze a hodnotu v tomto poli se zobrazí jako pouze **Windows**. Toto je pole jen pro čtení, který je nastaven při vytváření projektu.

- **Verze sady Windows SDK**

   Pro cílovou platformu Windows určuje verzi sady Windows SDK, které vyžaduje váš projekt. Při instalaci úlohy pro C++ s použitím instalačního programu sady Visual Studio, nainstaluje se také požadovaných součástí sady Windows SDK. Pokud máte další verze sady Windows SDK ve vašem počítači, se zobrazí v rozevírací nabídce každou verzi sady SDK nástroje, které jste nainstalovali.

   Chcete-li cílit na Windows 7 nebo Windows Vista, použijte hodnotu **8.1**, protože Windows SDK 8.1 je zpětně kompatibilní pro tyto platformy. Kromě toho byste měli definovat má hodnotu vhodnou pro **_WIN32_WINNT** v targetver.h. Pro Windows 7, který je 0x0601. Zobrazit [úpravy maker WINVER a _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

   Můžete nainstalovat sadu nástrojů platformy Windows XP součástí sady Visual Studio používat aktuální verzi knihovny k sestavení projektů Windows XP a Windows 2003 Server. Informace o tom, jak získat a používat touto sadou nástrojů platformy najdete v tématu [konfigurace aplikací pro Windows XP](../build/configuring-programs-for-windows-xp.md). Další informace o změně sada nástrojů platformy najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- **Cílové platformy Min. Verze**

   Určuje nejnižší verze platformy, které můžete spouštět projekt. Tato vlastnost se zobrazí jenom v případě, že typ projektu podporuje, například v projektech Windows Universal. Pokud vaše aplikace v novější verzi sady Windows SDK můžete využít výhod funkcí, ale může být stále spuštěny na starší verze bez těchto funkcí, třeba s určitou ztrátou funkce, která je pak hodnotu z těchto dvou vlastností lišit. Pokud váš kód tak, by měl zkontrolovat verzi platformy běží proti za běhu a ne pokusu o použití funkce, které nejsou k dispozici ve starší verzi platformy.

   Všimněte si, že Visual C++ nevynucuje tuto možnost. Přikládáme ji pro zajištění konzistence s jinými jazyky, jako je C# a JavaScript a jako vodítko pro každého, kdo používá váš projekt. Visual C++ nevygeneruje chybu, pokud používáte funkci, která není k dispozici v minimální verzi.

- **Výstupní adresář**

   Určuje adresář, do kterého nástroje, jako je například linker, umístí všechny konečné výstupní soubory, které jsou vytvořeny během procesu sestavení. Obvykle obsahuje výstupy nástrojů, jako je například linker, librarian nebo BSCMake. Ve výchozím nastavení, tato vlastnost je adresáři určeném argumentem makra $ $(SolutionDir) (konfigurace) \.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Zprostředkující adresář**

   Určuje adresář, do kterého nástroje, jako je například kompilátor, umístí všechny mezilehlé soubory vytvořené během procesu sestavení. Obvykle obsahuje výstupy nástrojů, jako je například kompilátor C/C++, MIDL a kompilátor prostředků. Ve výchozím nastavení, tato vlastnost je adresáři určeném argumentem – makro $(konfigurace) \.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Název cíle**

   Určuje název souboru vygenerovaného tímto projektem. Ve výchozím nastavení tato vlastnost je název souboru zadaného – makro $ (ProjectName).

- **Cílová přípona**

   Určuje příponu názvu souboru vygenerovaného tímto projektem; například .exe nebo .dll.

- **Přípony odstraňované při čištění**

   **Vyčistit** možnost (**sestavení** nabídky) odstraní soubory z mezilehlého adresáře, ve kterém je sestavena konfigurace projektu. Soubory s příponami zadanými pomocí této vlastnosti budou odstraněny při **Vyčistit** spuštění nebo při provádění opětovné sestavení. Kromě souborů s těmito příponami ve zprostředkujícím adresáři systém sestavení odstraní také všechny známé výstupy sestavení bez ohledu na to, kde jsou umístěny (včetně zprostředkujících výstupů, jako jsou například soubory .obj). Všimněte si, že je možné zadat zástupné znaky.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Soubor protokolu sestavení**

   Umožňuje určit jiné než výchozí umístění souboru protokolu, který je vytvořen při sestavení projektu. Výchozí umístění je určená .log makra $(IntDir) $(MSBuildProjectName).

   Chcete-li změnit umístění adresáře můžete použít projektová makra. Zobrazit [běžná makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md).

- **Sada nástrojů platformy**

   Umožňuje projekt cílit na jinou verzi knihovny Visual C++ a kompilátor. Projekty Visual C++ mohou cílit buď na výchozí sadu nástrojů nainstalované sady Visual Studio, nebo jeden z nástrojů nainstalována v předchozích verzích sady Visual Studio, včetně sady nástrojů, které vytvoříte spustitelné soubory, které můžete spustit v systému Windowx XP. Informace o změně sada nástrojů platformy najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- **Povolit spravované přírůstkové sestavení**

   Pro spravované projekty umožňuje detekovat externí viditelnosti, při generování sestavení. Pokud ke změně spravovaný projekt není viditelný pro jiné projekty, nejsou přetvořeny závislých projektů. To můžete výrazně vylepšit dobu sestavení v řešení, která zahrnují spravovaných projektů.

## <a name="project-defaults"></a>Výchozí vlastnosti projektu

Vlastnosti v oddíle Výchozí projektu představují výchozí vlastnosti, které můžete upravit. Definice pro tyto vlastnosti můžete najít v souborech .props v *instalační adresář*\VC\VCProjectDefaults.

- **Typ konfigurace**

   Existují vybírat z několika typů konfigurace:

   - **Aplikace (.exe)**

      Zobrazí sadu nástrojů linkeru (kompilátor C/C++, MIDL, kompilátor prostředků, Linker, BSCMake, generátor Proxy webové služby XML, vlastní sestavení, události prebuild, prelink a postbuild).

   - **Dynamická knihovna (.dll)**

      Zobrazí sadu nástrojů linkeru, určuje možnost/DLL linkeru a přidá definici _windll do CL.

   - **Soubor pravidel**

      Zobrazí sadu nástrojů makefile (NMake).

   - **Statická knihovna (.lib)**

      Zobrazí sadu nástrojů librarian (stejné jako sadu nástrojů linkeru, s výjimkou nahrazení nástroje librarian pro linker a vynechání generátoru Proxy webové služby XML).

   - **Nástroj**

      Zobrazí sadu nástrojů nástroje (MIDL, vlastní sestavení, události prebuild, postbuild).

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Použití knihovny MFC**

   Určuje, zda projekt knihovny MFC bude propojovat staticky nebo dynamicky ke knihovně MFC DLL. Můžete vybrat projekty bez knihovny MFC **použít standardní knihovny Windows** k propojení s různými knihovnami Win32, které jsou zahrnuty při použití knihovny MFC.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Použití knihovny ATL**

   Určuje, zda projekt knihovny ATL bude propojovat staticky nebo dynamicky ATL. KNIHOVNY DLL. Pokud zadáte cokoli jiného než **Nepoužívat ATL**, definovat se přidají do kompilátoru **příkazového řádku** stránku vlastností.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>.

- **Znaková sada**

   Definuje, zda by měla být nastavena _UNICODE nebo _MBCS. Kde je to vhodné, ovlivňuje také vstupní bod linkeru.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Podpora modulu CLR**

   Způsobí, že [/CLR](../build/reference/clr-common-language-runtime-compilation.md) použití možnosti kompilátoru.

   Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **Cílové verze rozhraní .NET**

   Ve spravovaných projektech určuje verze rozhraní .NET framework na cíl.

- **Celková optimalizace programu**

   Určuje, [/GL](../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru a [parametru/LTCG](../build/reference/ltcg-link-time-code-generation.md) – možnost linkeru. Ve výchozím nastavení to je zakázaná pro konfiguraci ladění a povolit pro maloobchodní konfigurace.

- **Podpora aplikací pro Windows Store**

   Určuje, zda tento projekt podporuje aplikace Windows Runtime (univerzální platformu Windows). Další informace najdete v tématu [/ZW (kompilace Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md)a ve středisku pro vývojáře Windows.

## <a name="see-also"></a>Viz také:

[Stránky vlastností](../ide/property-pages-visual-cpp.md)