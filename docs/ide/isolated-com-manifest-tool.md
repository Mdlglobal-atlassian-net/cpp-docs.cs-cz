---
title: Nástroj manifest izolované vlastnosti modelu COM (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c425a71f8bb8a7972ade29fb0d18cf3eab7debb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Izolované modelu COM, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností
Pomocí tohoto dialogového okna zadejte **izolované COM** možnosti pro [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Pro přístup k toto dialogové okno stránky vlastností, otevřete stránku vlastností projektu nebo seznam vlastnosti. Rozbalte **Nástroj Manifest** pod uzlem **společných vlastností**a potom vyberte **izolované COM**.  
  
## <a name="task-list"></a>Seznam úloh  
  
-   [Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Soubor knihovny typů**  
 Pomocí možnosti/tlb lze zadat název souboru knihovny typu (souboru .tlb), který nástroj manifestu použije k vygenerování souboru manifestu.  
  
 **Soubor skriptu registrátora**  
 Používá rgs zadat název souboru skriptu registrátora (.rgs soubor), který nástroj manifestu použije k vygenerování souboru manifestu.  
  
 **Název souboru komponenty**  
 Pomocí možnosti/dll lze zadat název prostředku, který manifestu nástroj vygeneruje. Musíte zadat hodnotu pro tuto vlastnost při hodnoty pro buď **soubor knihovny typu** nebo **soubor skriptu registrátora** nejsou zadány.  
  
 **Soubor nahrazení**  
 Používá replacements k zadejte úplnou cestu k souboru, který obsahuje hodnoty pro replaceable řetězce v souboru.  
  
## <a name="see-also"></a>Viz také  
 [Izolované aplikace](http://msdn.microsoft.com/library/aa375190)   
 [ClickOnce – Manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)   
 [Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)   