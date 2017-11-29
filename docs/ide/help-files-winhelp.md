---
title: "Soubory nápovědy (WinHelp) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a5036aa329c0b4004bd7ada724c62e1a1669f050
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="help-files-winhelp"></a>Soubory nápovědy (WinHelp)
Následující soubory jsou vytvořeny po přidání WinHelp typu nápovědy k aplikaci tak, že vyberete **Kontextová nápověda** zaškrtávací políčko a potom vyberete **WinHelp formátu** v [Upřesňující funkce](../mfc/reference/advanced-features-mfc-application-wizard.md) stránky Průvodce aplikací MFC.  
  
|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*HPJ|*Projname*\hlp|Zdrojové soubory|Soubor nápovědy projektu používá kompilátoru nápovědu k vytvoření programu nebo soubor nápovědy ovládacího prvku.|  
|*Projname*.rtf|*Projname*\hlp|Soubory nápovědy|Obsahuje informace o úpravách souboru HPJ a témata šablony, které můžete upravit.|  
|*Projname*.cnt|*Projname*\hlp|Soubory nápovědy|Poskytuje struktury **obsah** okna nápovědy k systému Windows.|  
|Makehelp.bat|*Projname*|Zdrojové soubory|Používá systém pro sestavení projektu nápovědy během kompilace projektu.|  
|PRINT.RTF|*Projname*\hlp|Soubory nápovědy|Vytvoří, pokud projekt zahrnuje podporu tisku (výchozí). Popisuje příkazy pro tisk a dialogová okna.|  
|*.bmp|*Projname*\hlp|Zdrojové soubory|Obsahovat bitových kopií pro jiné témata nápovědy.|  
  
 Můžete přidat podporu nápovědy do projektu MFC ovládací prvek ActiveX výběrem **Generovat soubory nápovědy** v [nastavení aplikace](../mfc/reference/application-settings-mfc-activex-control-wizard.md) kartě Průvodce ovládacím prvkem ActiveX knihovny MFC. Následující soubory se přidají do projektu, když přidáte podporu nápovědy do ovládacího prvku ActiveX knihovny MFC:  
  
|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*HPJ|*Projname*\hlp|Zdrojové soubory|Soubor projektu používá kompilátoru nápovědu k vytvoření programu nebo soubor nápovědy ovládacího prvku.|  
|*Projname*.rtf|*Projname*\hlp|Project|Obsahuje informace o úpravách souboru HPJ a témata šablony, které můžete upravit.|  
|Makehelp.bat|*Projname*|Zdrojové soubory|Používá systém pro sestavení projektu nápovědy během kompilace projektu.|  
|Bullet.bmp|*Projname*|Zdrojové soubory|Používá standardní témata nápovědy k představují seznamy s odrážkami.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)