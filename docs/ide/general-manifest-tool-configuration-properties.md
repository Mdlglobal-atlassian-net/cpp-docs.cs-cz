---
title: Manifest, vlastnosti konfigurace nástroje (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs:
- C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef1eb1c0c1ee8c9fb2814bc7cd808ea2e524b8a4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200330"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Obecné, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností projektu
Můžete nastavit obecné možnosti dialogovému oknu [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
 Pro přístup k této dialogové okno stránky vlastností, otevřete stránky vlastností projektu, nebo seznam vlastností. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a pak vyberte **Obecné**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Potlačit úvodní nápis**  
 **Ano (/ nologo)** Určuje, že budou standardní data o autorských právech společnosti Microsoft při spuštění nástroje manifestu skryty. Tuto možnost použijte k potlačení nežádoucí výstup v souborech protokolů, když spustíte mt.exe jako součást procesu sestavení nebo z prostředí sestavení.  
  
 **Podrobný výstup**  
 **Ano (/ verbose)** Určuje, že informace o dalších sestavení se zobrazí během generování manifestu.  
  
 **Identita sestavení**  
 Možnost/identity používá k určení řetězec identity, který se skládá z atributů pro [ \<assemblyIdentity > Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Řetězec identity začíná hodnotu `name` atribut a je následována *atribut* = *hodnotu* dvojice. Atributy v řetězec identity jsou oddělené čárkou.  
  
 Tady je příklad řetězce identity:  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – Manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)   
 [Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)   