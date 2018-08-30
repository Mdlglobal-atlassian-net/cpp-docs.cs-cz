---
title: CWinApp a Průvodce aplikací MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a716119acc857419dcf128c39ab2c20921cd2d4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211388"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp a průvodce aplikací MFC
Při vytváření kostry aplikace, Průvodce aplikací MFC deklaruje Aplikační třída odvozená z [CWinApp](../mfc/reference/cwinapp-class.md). Průvodce aplikací MFC také vygeneruje soubor implementace, která obsahuje následující položky:  
  
-   Mapy zpráv pro třídu aplikace.  
  
-   Prázdná třída konstruktor.  
  
-   Proměnná, která deklaruje pouze objekt třídy.  
  
-   Standardní implementace vaší `InitInstance` členskou funkci.  
  
 Třída aplikace je umístěn v záhlaví projektu a hlavní zdrojových souborů. Názvy třídy a soubory vytvořené jsou založeny na název projektu, který zadáte v průvodci MFC aplikace. Nejjednodušší způsob, jak zobrazit kód pro tyto třídy je prostřednictvím [zobrazení tříd](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
 Standardní implementace a mapování zpráv zadaný jsou dostatečné pro celou řadu účelů, ale můžete je upravit podle potřeby. Nejzajímavější z těchto implementací je `InitInstance` členskou funkci. Obvykle přidáte kód do základní implementace `InitInstance`.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp Aplikace – třída](../mfc/cwinapp-the-application-class.md)   
 [Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)   
 [Speciální služby CWinApp](../mfc/special-cwinapp-services.md)

