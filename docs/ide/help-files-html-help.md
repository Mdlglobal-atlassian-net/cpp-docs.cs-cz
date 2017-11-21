---
title: "Soubory (Nápověda jazyka HTML) nápovědy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b97c73514d534ba6092c8b1c3ec5cfa676500538
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="help-files-html-help"></a>Soubory nápovědy (Nápověda jazyka HTML)
Následující soubory se vytvoří při přidání HTML – Nápověda typu nápovědy do aplikace tak, že vyberete **Kontextová nápověda** zaškrtávací políčko a potom vyberete **formát HTML – Nápověda** v [Upřesňující funkce](../mfc/reference/advanced-features-mfc-application-wizard.md) stránky Průvodce aplikací MFC.  
  
|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*hhp|*Projname*\hlp|soubory nápovědy HTML|Soubor projektu nápovědy. Obsahuje data potřebná k zkompilovat soubory nápovědy do souboru .hxs nebo soubor CHM..|  
|*Projname*.hhk|*Projname*\hlp|soubory nápovědy HTML|Obsahuje index témat nápovědy.|  
|*Projname*.hhc|*Projname*\hlp|soubory nápovědy HTML|Obsah nápovědy projektu.|  
|Makehtmlhelp.bat|*Projname*|Zdrojové soubory|Používá systém pro sestavení projektu nápovědy během kompilace projektu.|  
|Afxcore.htm|*Projname*\hlp|Témata nápovědy HTML|Obsahuje standardní témata nápovědy pro standardní příkazy MFC a objektů na obrazovce. Přidáte vlastní témata nápovědy k tomuto souboru.|  
|Afxprint.htm|*Projname*\hlp|Témata nápovědy HTML|Obsahuje témata nápovědy pro příkazy tisku.|  
|*.jpg; \*.gif|*Projname*\hlp\Images|Zdrojové soubory|Obsahovat bitových kopií pro jiné témata nápovědy.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)