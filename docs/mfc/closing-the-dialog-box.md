---
title: "Zavření dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4c311a8d09ac3e1329b495fc321028e9f674993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna
Modální dialogové okno zavře, když uživatel vybere jeden z jeho tlačítka, obvykle na tlačítko OK nebo na tlačítko Storno. Klepněte na tlačítko OK nebo Storno způsobí, že systému Windows pro odesílání objektu dialogového okna **BN_CLICKED** zpráva oznámení ovládacího prvku pomocí tlačítka je buď ID, **IDOK** nebo **IDCANCEL**. `CDialog`poskytuje výchozí funkce obslužných rutin pro tyto zprávy: `OnOK` a `OnCancel`. Výchozí volání obslužné rutiny `EndDialog` – členská funkce zavřete dialogové okno. Můžete také volat `EndDialog` z vlastního kódu. Další informace najdete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkce člena třídy `CDialog` v *odkaz knihovny MFC*.  
  
 Uspořádat pro zavření a odstraňování nemodální dialogové okno, přepsání `PostNcDestroy` a vyvolání **odstranit** operátor na **to** ukazatel. [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md) vysvětluje, co se stane dále.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

