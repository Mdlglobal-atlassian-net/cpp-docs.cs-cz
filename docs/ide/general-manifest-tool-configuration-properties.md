---
title: Manifest nástroj pro konfiguraci vlastnosti (Visual C++) | Microsoft Docs
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
ms.openlocfilehash: 1953e7c37c07f66845510efe037015a537aa7baa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Obecné, Nástroj Manifest, vlastnosti konfigurace &lt;Projectname&gt; dialogové okno stránky vlastností
Pomocí tohoto dialogového okna Obecné možnosti pro [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Pro přístup k toto dialogové okno stránky vlastností, otevřete stránku vlastností projektu nebo seznam vlastnosti. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a potom vyberte **Obecné**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Potlačit úvodní nápis při spouštění**  
 **Ano (/ nologo)** Určuje, že budou standardní údaje o autorských právech Microsoft skryty při spuštění nástroje manifestu. Tuto možnost použijte k potlačení nežádoucí výstup do souborů protokolu, když spustíte mt.exe jako součást procesu sestavení nebo z prostředí sestavení.  
  
 **Podrobný výstup**  
 **Ano (/ verbose)** Určuje, že další sestavení informace se zobrazí při generování manifestu.  
  
 **Identita sestavení**  
 Pomocí možnosti/identity lze zadat jako řetězec identity, který zahrnuje atributy pro [ \<assemblyIdentity > Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Řetězec identity začíná hodnota `name` atribut a je následován *atribut* = *hodnotu* páry. Atributy v řetězec identity jsou odděleny čárkami.  
  
 Následuje příklad řetězce identity:  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – Manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)   
 [Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)   