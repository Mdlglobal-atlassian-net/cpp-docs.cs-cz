---
title: Vytvoření vlastní třídy dialogového okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d70f27639344fd00a2e99ad79bf2db166f3270a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

