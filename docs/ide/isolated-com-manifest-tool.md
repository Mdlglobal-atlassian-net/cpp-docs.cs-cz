---
title: "Nástroj manifest izolované vlastnosti modelu COM (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs: C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 043420b5d948f17c3764d985262a88f082277d9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Izolované modelu COM, Nástroj Manifest, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností
Pomocí tohoto dialogového okna zadejte **izolované COM** možnosti pro [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Pro přístup k toto dialogové okno stránky vlastností, otevřete stránku vlastností projektu nebo seznam vlastnosti. Rozbalte **Nástroj Manifest** pod uzlem **společných vlastností**a potom vyberte **izolované COM**.  
  
## <a name="task-list"></a>Seznam úloh  
  
-   [Postupy: sestavení izolované aplikace pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
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
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)   