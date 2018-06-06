---
title: NMake – stránka vlastností (Windows C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs:
- C++
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f156d69467f00c4c4a62ec84d3b870e2999d7115
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33327457"
---
# <a name="nmake-property-page"></a>NMake – stránka vlastností
**NMake** stránka vlastností umožňuje zadat nastavení sestavení pro projekty NMake.  
  
 Další informace o projekty NMake najdete v tématu [vytvoření projektu souboru pravidel](../ide/creating-a-makefile-project.md). Projekty MakeFile non_Windows, najdete v tématu [vlastnosti projektu souboru pravidel (Linux C++)](../linux/prop-pages/makefile-linux.md), [obecné vlastnosti projektu (Android C++ Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page) nebo [NMake vlastnosti (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page).
  
 **NMake** vlastnost stránka obsahuje následující vlastnosti.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Sestavení příkazového řádku**  
 Určuje příkaz, který se spustí, když **sestavení** po kliknutí na na **sestavení** nabídky.  
  
 **Znovu vytvořit všechny příkazového řádku**  
 Určuje příkaz, který se spustí, když **znovu vytvořit všechny** po kliknutí na na **sestavení** nabídky.  
  
 **Vyčištění příkazového řádku**  
 Určuje příkaz, který se spustí, když **Vyčistit** po kliknutí na na **sestavení** nabídky.  
  
 **Output**  
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
 [Postupy: Povolení technologie IntelliSense pro projekty souborů pravidel](../ide/how-to-enable-intellisense-for-makefile-projects.md)