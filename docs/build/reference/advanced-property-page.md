---
title: Stránka rozšířené vlastnosti (projekt)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328416"
---
# <a name="advanced-property-page"></a>Stránka rozšířené vlastnosti

Stránka vlastností Upřesnit je k dispozici v sadě Visual Studio 2019 a novějších.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Upřesnit vlastnosti

- **Cílová přípona souboru**

   Určuje příponu souboru, která má být pro výstup sestavení. Výchozí hodnota **.exe** pro aplikace, **.lib** pro statické knihovny a **knihovna DLL** pro knihovny DLL.

- **Rozšíření odstranit při čištění**

   Možnost **Vyčistit** (**Nabídka sestavení)** odstraní soubory z mezilehlého adresáře, kde je vytvořena konfigurace projektu. Soubory s rozšířeními zadanými touto vlastností budou odstraněny při spuštění **aplikace Clean** nebo při opětovném sestavení. Kromě souborů těchto rozšíření v zprostředkujícím adresáři systém sestavení také odstraní všechny známé výstupy sestavení bez ohledu na to, kde se nachází (včetně zprostředkujících výstupů, jako jsou soubory OBJ). Všimněte si, že můžete zadat zástupné znaky.

   Chcete-li programově přistupovat <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>k této vlastnosti, naleznete v tématu .

- **Soubor protokolu sestavení**

   Umožňuje zadat jiné než výchozí umístění souboru protokolu, který je vytvořen při každém sestavení projektu. Výchozí umístění je určeno makry $(IntDir)$(MSBuildProjectName).log.

   Makra projektu můžete použít ke změně umístění adresáře. Viz [Společná makra pro příkazy a vlastnosti sestavení](common-macros-for-build-commands-and-properties.md).

- **Upřednostňovaná architektura nástrojů sestavení**

   Určuje, zda se mají používat nástroje sestavení x86 nebo x64.

- **Použití ladicích knihoven**

   Určuje, zda má být sestavení ladění nebo uvolnění k vytvoření.

- **Povolit sestavení Unity (JUMBO)**

   Umožňuje proces sestavení, kde mnoho zdrojových souborů Jazyka C++ jsou sloučeny do jednoho nebo více "jednoty" soubory před kompilací ke zlepšení výkonu sestavení. Nesouvisí s herní engine Unity.

- **Použití knihovny MFC**

   Určuje, zda bude projekt knihovny MFC staticky nebo dynamicky propojen s knihovnou DLL knihovny MFC. Projekty bez knihovny MFC můžete vybrat **použít standardní knihovny systému Windows** pro propojení s různými knihovnami Win32, které jsou zahrnuty při použití knihovny MFC.

   Chcete-li programově přistupovat <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>k této vlastnosti, naleznete v tématu .

- **Znaková sada**

   Definuje, zda má být nastaveno _UNICODE nebo _MBCS. Také ovlivňuje vstupní bod propojovacího systému, kde je to vhodné.

   Chcete-li programově přistupovat <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>k této vlastnosti, naleznete v tématu .

- **Optimalizace celého programu**

   Určuje možnost kompilátoru [/GL](gl-whole-program-optimization.md) a [/LTCG](ltcg-link-time-code-generation.md) linker. Ve výchozím nastavení je tato možnost zakázána pro konfigurace ladění a povolena pro konfigurace maloobchodu.

- **Verze sady nástrojů MSVC**

   Určuje plnou verzi sady nástrojů MSVC, která bude použita k sestavení projektu. Pokud máte nainstalovány různé verze aktualizace a náhledu sady nástrojů, můžete zde určit, který z nich se má použít.

## <a name="ccli-properties"></a>Vlastnosti c++/CLI

- **Podpora common language runtime**

   Způsobí, že [/clr](clr-common-language-runtime-compilation.md) kompilátor možnost použít.

   Chcete-li programově přistupovat <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>k této vlastnosti, naleznete v tématu .

- **Verze cílového rozhraní .NET**

   Ve spravovaných projektech určuje verzi rozhraní .NET framework, na kterou má být cílit.

- **Povolení spravovaného přírůstkového sestavení**

   U spravovaných projektů to umožňuje detekci externí viditelnosti při generování sestavení. Pokud změna spravovaného projektu není viditelná pro jiné projekty, nejsou závislé projekty znovu sestaveny. To může výrazně zlepšit dobu sestavení v řešeních, která zahrnují spravované projekty.

::: moniker-end
