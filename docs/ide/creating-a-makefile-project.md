---
title: "Vytvoření projektu souboru pravidel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.makefile.project
dev_langs: C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 834475840fbe20a0d6938c563f3541c294e09bee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-makefile-project"></a>Vytvoření projektu souboru pravidel
Máte-li projekt, který jste vytvořili z příkazového řádku se souborem pravidel, vývojové prostředí Visual Studio jej nerozpozná. K otevření a sestavení, váš projekt pomocí [!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)], Visual Studio Professional nebo Visual Studio Express pro Windows Desktop, nejprve vytvořit prázdný projekt výběrem šablony projektu souboru pravidel. Tento projekt potom můžete použít k sestavení projektu z vývojového prostředí Visual Studio.  
  
 Projekt nezobrazí žádné soubory v Průzkumníku řešení. Projekt určuje nastavení sestavení, která se projeví na stránce vlastností projektu.  
  
 Výstupní soubor zadaný v projektu nemá žádný vliv na název, který generuje skript sestavení; deklaruje pouze záměr.  
  
### <a name="to-create-a-makefile-project"></a>Vytvoření projektu Makefile  
  
1.  Postupujte podle pokynů v tématu nápovědy [vytvoření projektu pomocí Průvodce aplikací Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  V **nový projekt** dialogové okno, vyberte **projektem souboru pravidel** v podokně šablon otevřete průvodce.  
  
3.  V [nastavení aplikace](../ide/application-settings-makefile-project-wizard.md) stránky, zadejte příkaz, výstup, vyčistit a znovu sestavte informace.  
  
4.  Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nově vytvořený projekt v **Průzkumníku řešení**.  
  
 Na stránce vlastností projektu můžete zobrazit a upravit jeho vlastnosti. V tématu [nastavení vlastností projektu Visual C++](../ide/working-with-project-properties.md) informace o zobrazení stránky vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce projektem souboru pravidel](../ide/makefile-project-wizard.md)   
 [Speciální znaky v souboru pravidel](../build/special-characters-in-a-makefile.md)   
 [Obsah souboru pravidel](../build/contents-of-a-makefile.md)