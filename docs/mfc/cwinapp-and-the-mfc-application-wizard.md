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
ms.openlocfilehash: 59fcd3f00fb8998cf90c88d574b9d22051cb4305
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687781"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp a průvodce aplikací MFC
Při vytváření kostry aplikace, Průvodce aplikací MFC deklaruje Aplikační třída odvozená z [CWinApp](../mfc/reference/cwinapp-class.md). Průvodce aplikací MFC také vygeneruje soubor implementace, která obsahuje následující položky:  
  
-   Mapy zpráv pro třídu aplikace.  
  
-   Prázdná třída konstruktor.  
  
-   Proměnná, která deklaruje pouze objekt třídy.  
  
-   Standardní implementace vaší `InitInstance` členskou funkci.  
  
 Třída aplikace je umístěn v záhlaví projektu a hlavní zdrojových souborů. Názvy třídy a soubory vytvořené jsou založeny na název projektu, který zadáte v průvodci MFC aplikace. Nejjednodušší způsob, jak zobrazit kód pro tyto třídy je prostřednictvím [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Standardní implementace a mapování zpráv zadaný jsou dostatečné pro celou řadu účelů, ale můžete je upravit podle potřeby. Nejzajímavější z těchto implementací je `InitInstance` členskou funkci. Obvykle přidáte kód do základní implementace `InitInstance`.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp Aplikace – třída](../mfc/cwinapp-the-application-class.md)   
 [Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)   
 [Speciální služby CWinApp](../mfc/special-cwinapp-services.md)

