---
title: "Zavření dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7cd57819c5ab462b0310162d3c043c5f39d2a69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna
Modální dialogové okno zavře, když uživatel vybere jeden z jeho tlačítka, obvykle na tlačítko OK nebo na tlačítko Storno. Klepněte na tlačítko OK nebo Storno způsobí, že systému Windows pro odesílání objektu dialogového okna **BN_CLICKED** zpráva oznámení ovládacího prvku pomocí tlačítka je buď ID, **IDOK** nebo **IDCANCEL**. `CDialog`poskytuje výchozí funkce obslužných rutin pro tyto zprávy: `OnOK` a `OnCancel`. Výchozí volání obslužné rutiny `EndDialog` – členská funkce zavřete dialogové okno. Můžete také volat `EndDialog` z vlastního kódu. Další informace najdete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkce člena třídy `CDialog` v *odkaz knihovny MFC*.  
  
 Uspořádat pro zavření a odstraňování nemodální dialogové okno, přepsání `PostNcDestroy` a vyvolání **odstranit** operátor na **to** ukazatel. [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md) vysvětluje, co se stane dále.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

