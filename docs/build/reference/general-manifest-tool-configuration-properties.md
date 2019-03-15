---
title: Konfigurace vlastnosti manifestu nástroje (C++ dokumentačních komentářů)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
ms.openlocfilehash: 9acdb7f5c934a8cabdd1803074778ac9f01f4960
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823377"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Obecné, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu

Můžete nastavit obecné možnosti dialogovému oknu [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a pak vyberte **Obecné**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Potlačit úvodní nápis**

   **Ano (/ nologo)** Určuje, že budou standardní data o autorských právech společnosti Microsoft při spuštění nástroje manifestu skryty. Tuto možnost použijte k potlačení nežádoucí výstup v souborech protokolů, když spustíte mt.exe jako součást procesu sestavení nebo z prostředí sestavení.

- **Podrobný výstup**

   **Ano (/ verbose)** Určuje, že informace o dalších sestavení se zobrazí během generování manifestu.

- **Identita sestavení**

   Možnost/identity používá k určení řetězec identity, který se skládá z atributů pro [ \<assemblyIdentity > Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Řetězec identity začíná hodnotu `name` atribut a je následována *atribut* = *hodnotu* dvojice. Atributy v řetězec identity jsou oddělené čárkou.

   Tady je příklad řetězce identity:

   `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="see-also"></a>Viz také:

[ClickOnce – manifest aplikace ](/visualstudio/deployment/clickonce-application-manifest)<br>
[Stránky vlastností nástroje manifest](manifest-tool-property-pages.md)<br>
[Nastavení kompilátoru jazyka C++ a vlastnosti v sadě Visual Studio sestavení](../working-with-project-properties.md)
