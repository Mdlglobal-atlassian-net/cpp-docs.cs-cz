---
title: "CWinApp a Průvodce aplikací MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1e1eb73bf0b4a3eb91be63f3953959fa67e0737
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp a průvodce aplikací MFC
Při vytváření kostru aplikace, Průvodce aplikací MFC deklaruje Aplikační třída odvozená z [CWinApp](../mfc/reference/cwinapp-class.md). Průvodce aplikací MFC také generuje soubor implementace, která obsahuje následující položky:  
  
-   Mapy zpráv pro třídu aplikace.  
  
-   Prázdná třída – konstruktor.  
  
-   Proměnná, který deklaruje ten a pouze objekt třídy.  
  
-   Standardní implementace objektu vaší `InitInstance` – členská funkce.  
  
 Třída aplikace je umístěn v záhlaví projektu a hlavní zdrojové soubory. Názvy tříd a soubory vytvořené jsou založené na název projektu, který uvedete, Průvodce aplikací MFC. Nejjednodušší způsob, jak zobrazit kód pro tyto třídy je prostřednictvím [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
 Standardní implementace a mapy zpráv zadaný jsou pro mnoho účely, ale můžete je upravit podle potřeby. Většina zajímavé tyto implementace je `InitInstance` – členská funkce. Obvykle přidáte kód na kosterního implementaci `InitInstance`.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – Třída aplikace](../mfc/cwinapp-the-application-class.md)   
 [Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)   
 [Speciální služby CWinApp](../mfc/special-cwinapp-services.md)

