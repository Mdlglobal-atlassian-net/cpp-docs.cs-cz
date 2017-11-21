---
title: "Manifest nástroj vstupní a výstupní vlastnosti (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
dev_langs: C++
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6042a480eef506af736ad958643288efa67402d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Vstup a výstup, Manifest nástroj, vlastnosti konfigurace, &lt;Projectname&gt; dialogové okno stránky vlastností
Pomocí tohoto dialogového okna vstupní a výstupní možnosti pro [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Pro přístup k toto dialogové okno stránky vlastností, otevřete stránku vlastností projektu nebo seznam vlastnosti. Rozbalte **Nástroj Manifest** pod uzlem **vlastnosti konfigurace**a potom vyberte **vstup a výstup**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Další soubory manifestu**  
 Používá **/manifest** možnost určení úplné cesty další manifestu souborů, které bude zpracovávat nástroje manifestu nebo sloučení. Úplné cesty jsou oddělené středníkem.  
  
 **Vstupní prostředek manifestů**  
 Používá **/inputresource** možnost zadat úplnou cestu prostředku typu RT_MANIFEST pro vstup do manifestu nástroje. Cesta může následovat ID zadaný prostředek. Příklad:  
  
 `dll_with_manifest.dll;#1`  
  
 ID prostředku je volitelný a výchozí pro CREATEPROCESS_MANIFEST_RESOURCE_ID ve winuser.  
  
 **Vložení manifestu**  
 **Ano** Určuje, že systém projektu vloží soubor manifestu aplikace do sestavení.  
  
 **Ne** Určuje, že systém projektu se vytvoří soubor manifestu aplikace jako samostatný soubor.  
  
 **Výstupní soubor manifestu**  
 Určuje název výstupního souboru manifestu. Tato vlastnost je nepovinná, pokud pouze jeden soubor manifestu je provozována na nástrojem manifestu.  
  
 **Soubor manifestu prostředků**  
 Určuje výstupní soubory prostředků použít pro vložení manifestu do výstupu projektu @.  
  
 **Generování souborů katalogu**  
 Používá **/makecdfs** můžete určit, že nástroj manifestu vygeneruje definice soubory katalogu (), které se používají k provádění katalogů.  
  
 **Generovat Manifest z ManagedAssembly**  
 Generuje manifest ze spravovaných sestavení. (**- managedassemblyname:***souboru*).  
  
 **Potlačit Dependency – Element**  
 Používá se **- managedassembly** možnost. Tato značka potlačí generování závislosti elementů ve výsledném manifestu.  
  
 **Vygenerovat značky kategorie**  
 Používá se **- managedassembly** možnost. Tato značka způsobí, že generování značek kategorie.  
  
 **Povolit sledování bodů na PALEC**  
 Určuje, jestli je aplikace využívající technologii DPI. Ve výchozím nastavení je **Ano** pro projekty MFC a **ne** jinak, protože pouze projekty MFC mají vestavěné sledování bodů na PALEC. Můžete přepsat nastavení pro **Ano** Pokud přidáte kód pro zpracování různých nastavení DPI. Přibližné nebo malý, pokud je nastavena jako palec Pokud není, může být aplikace.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – Manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)   
 [Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)   