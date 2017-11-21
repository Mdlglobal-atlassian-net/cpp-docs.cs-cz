---
title: "Vytvoření vlastní třídy dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd80d55df3ae9adc4a586d1cc5387ee6d1f53282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-your-dialog-class"></a>Vytvoření vlastní třídy dialogového okna
Pro každý dialogové okno v programu vytvořte novou třídu dialogové okno pro práci s prostředku dialogového okna.  
  
 [Přidání třídy](../ide/adding-a-class-visual-cpp.md) vysvětluje, jak vytvořit nové třídy dialogového okna. Když vytvoříte pomocí Průvodce přidáním třídy dialogového okna, zapíše následující položky. H a. CPP souborů, které můžete zadat:  
  
 V. Soubor H:  
  
-   Deklarace třídy pro třídy dialogového okna. Odvození třídy z [CDialog](../mfc/reference/cdialog-class.md).  
  
 V. Soubor CPP:  
  
-   Mapy zpráv pro třídu.  
  
-   Standardní konstruktor pro dialogové okno.  
  
-   Přepsání [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) – členská funkce. Upravte tuto funkci. Používá se pro dialogové okno Možnosti výměna a ověření dat popsané později v [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření třídy dialogového okna s použitím průvodců kódem](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

