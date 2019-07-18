---
title: Pokročilá stránka vlastností (projekt)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315519"
---
# <a name="advanced-property-page"></a>Upřesnit stránku vlastností

Stránka Upřesnit vlastnost je k dispozici v aplikaci Visual Studio 2019 nebo novější.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Upřesnit vlastnosti

- **Přípona cílového souboru**

   Určuje příponu souboru, která má být použita pro výstup sestavení. Ve výchozím nastavení je to **. exe** pro aplikace, **. lib** pro statické knihovny a **. dll** pro knihovny DLL.

- **Přípony k odstranění při čištění**

   Možnost **vyčistit** (nabídka**sestavení** ) odstraní soubory z mezilehlého adresáře, kde je vytvořena konfigurace projektu. Soubory s příponami, které jsou zadané pomocí této vlastnosti, se odstraní, když se spustí **Vyčištění** nebo když provedete opětovné sestavení. Kromě souborů těchto rozšíření v zprostředkujícím adresáři systém sestavení také odstraní jakýkoliv známý výstup sestavení bez ohledu na to, kde se nachází (včetně mezilehlých výstupů, jako jsou soubory. obj). Všimněte si, že můžete zadat zástupné znaky.

   Chcete-li programově získat přístup k <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>této vlastnosti, přečtěte si téma.

- **Soubor protokolu sestavení**

   Umožňuje zadat jiné než výchozí umístění souboru protokolu, který se vytvoří při každém sestavení projektu. Výchozí umístění je zadáno pomocí makra $ (IntDir) $ (MSBuildProjectName) $ (). log.

   Můžete použít makra projektu ke změně umístění adresáře. Viz [společná makra pro příkazy a vlastnosti buildu](common-macros-for-build-commands-and-properties.md).

- **Upřednostňovaná architektura nástrojů sestavení**

   Určuje, jestli se mají používat nástroje pro sestavení x86 nebo x64.

- **Použití knihoven ladění**

   Určuje, zda se má vytvořit sestavení pro ladění nebo vydání.

- **Povolit sestavení Unity (JUMBO)**

   Povoluje proces sestavení, kde je C++ mnoho zdrojových souborů sloučeno do jednoho nebo více souborů Unity před kompilací pro zlepšení výkonu sestavení. Nesouvisí s herním modulem Unity.

- **Použití knihovny MFC**

   Určuje, zda projekt knihovny MFC bude staticky nebo dynamicky propojen s knihovnou MFC DLL. Projekty mimo knihovnu MFC mohou vybrat možnost **použít standardní knihovny Windows** pro propojení s různými knihovnami Win32, které jsou zahrnuty při použití knihovny MFC.

   Chcete-li programově získat přístup k <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>této vlastnosti, přečtěte si téma.

- **Znaková sada**

   Definuje, jestli se má nastavit _UNICODE nebo _MBCS. Také ovlivňuje vstupní bod linkeru, kde je to vhodné.

   Chcete-li programově získat přístup k <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>této vlastnosti, přečtěte si téma.

- **Optimalizace celého programu**

   Určuje možnost kompilátoru [/GL](gl-whole-program-optimization.md) a možnost linkeru [/LTCG](ltcg-link-time-code-generation.md) . Ve výchozím nastavení je tato možnost zakázána pro konfiguraci ladění a je povolena pro maloobchodní konfigurace.

- **Verze sady nástrojů MSVC**

   Určuje úplnou verzi sady nástrojů MSVC, která se použije k sestavení projektu. Pokud máte nainstalovanou různou verzi sady nástrojů pro aktualizace a verzi Preview, můžete určit, která z nich se má použít.

## <a name="ccli-properties"></a>C++/CLI – vlastnosti

- **Podpora modulu CLR (Common Language Runtime)**

   Způsobí použití možnosti kompilátoru [/CLR](clr-common-language-runtime-compilation.md) .

   Chcete-li programově získat přístup k <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>této vlastnosti, přečtěte si téma.

- **Cílová verze rozhraní .NET Framework**

   Ve spravovaných projektech určuje cílovou verzi rozhraní .NET Framework.

- **Povolit spravované přírůstkové sestavení**

   U spravovaných projektů to umožňuje detekci externí viditelnosti při generování sestavení. Pokud změna spravovaného projektu není viditelná pro jiné projekty, pak nejsou znovu sestaveny závislé projekty. To může výrazně zlepšit dobu sestavení v řešeních, která zahrnují spravované projekty.

::: moniker-end
