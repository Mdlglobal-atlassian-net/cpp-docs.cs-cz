---
title: "NMake – stránka vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs: C++
helpviewer_keywords: NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c487cf7218f11ba6a6a27ddcf5e7b6b575b1499
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-property-page"></a>NMake – stránka vlastností
**NMake** stránka vlastností umožňuje zadat nastavení sestavení pro projekty NMake.  
  
 Další informace o projekty NMake najdete v tématu [vytvoření projektu souboru pravidel](../ide/creating-a-makefile-project.md).  
  
 **NMake** vlastnost stránka obsahuje následující vlastnosti.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Sestavení příkazového řádku**  
 Určuje příkaz, který se spustí, když **sestavení** po kliknutí na na **sestavení** nabídky.  
  
 **Znovu vytvořit všechny příkazového řádku**  
 Určuje příkaz, který se spustí, když **znovu vytvořit všechny** po kliknutí na na **sestavení** nabídky.  
  
 **Vyčištění příkazového řádku**  
 Určuje příkaz, který se spustí, když **Vyčistit** po kliknutí na na **sestavení** nabídky.  
  
 **Výstup**  
 Určuje název souboru, který bude obsahovat výstup příkazového řádku. Ve výchozím nastavení je tento název souboru založen na název projektu.  
  
 **Definice preprocesoru**  
 Určuje žádné definice preprocesoru používají zdrojové soubory. Výchozí hodnota je určen podle aktuální platformě a konfigurace.  
  
 **Zahrnout cesty pro hledání**  
 Určuje adresáře, kde kompilátor vyhledává zahrnout soubory.  
  
 **Vynutit zahrnuje**  
 Určuje soubory, které preprocesor automaticky zpracuje, i když nejsou zahrnuty v souborech projektu.  
  
 **Cesta hledání sestavení**  
 Určuje adresáře, kde rozhraní .NET Framework vyhledává ho zkusí vyřešit sestavení .NET.  
  
 **Vynucené použití sestavení**  
 Určuje sestavení, které automaticky zpracuje rozhraní .NET Framework.  
  
 **Další možnosti**  
 Určuje dalších přepínačů technologie IntelliSense pro použití při analýze souborů C++.  
  
 Informace o tom, jak získat přístup **NMake** stránce vlastností, najdete v části [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
 Informace o tom, jak programově přístup členům tohoto objektu najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)   
 [Postupy: povolení technologie IntelliSense pro projekty Makefile](../ide/how-to-enable-intellisense-for-makefile-projects.md)