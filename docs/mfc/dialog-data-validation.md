---
title: "Ověřování dat dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58fbff4a5192d15a60cf3340ce762574947fb249
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dialog-data-validation"></a>Ověřování dat dialogového okna
Můžete zadat ověření kromě výměny dat voláním funkce DDV, jak je znázorněno v příkladu v [výměna dialogových dat](../mfc/dialog-data-exchange.md). `DDV_MaxChars` Volání v příkladu ověří, že řetězec zadaný v ovládacím prvku textového pole není delší než 20 znaků. Funkce DDV obvykle upozorní uživatele s okno se zprávou, pokud ověření selže a vloží zaměřuje na problematický ovládací prvek, uživatel může znovu zadat data. DDV funkce pro daný ovládací prvek musí být volána hned po funkce DDX pro stejný ovládací prvek.  
  
 Můžete také definovat vlastní vlastní rutiny DDX a DDV. Podrobnosti o tomto a dalších aspektů DDX a DDV najdete v tématu [MFC Technická poznámka 26](../mfc/tn026-ddx-and-ddv-routines.md).  
  
 [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) bude zapisovat všechny DDX a DDV volání v mapování dat za vás.  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno Data výměna a ověřování](../mfc/dialog-data-exchange-and-validation.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)   
 [Výměna dat dialogových oken](../mfc/dialog-data-exchange.md)
