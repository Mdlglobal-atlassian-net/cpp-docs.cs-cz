---
title: Zavření dialogového okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c800c204fd09057585064397d459f92c9ded272d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341742"
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna
Modální dialogové okno zavře, když uživatel vybere jeden z jeho tlačítka, obvykle na tlačítko OK nebo na tlačítko Storno. Klepněte na tlačítko OK nebo Storno způsobí, že systému Windows pro odesílání objektu dialogového okna **BN_CLICKED** zpráva oznámení ovládacího prvku pomocí tlačítka je buď ID, **IDOK** nebo **IDCANCEL**. `CDialog` poskytuje výchozí funkce obslužných rutin pro tyto zprávy: `OnOK` a `OnCancel`. Výchozí volání obslužné rutiny `EndDialog` – členská funkce zavřete dialogové okno. Můžete také volat `EndDialog` z vlastního kódu. Další informace najdete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkce člena třídy `CDialog` v *odkaz knihovny MFC*.  
  
 Uspořádat pro zavření a odstraňování nemodální dialogové okno, přepsání `PostNcDestroy` a vyvolání **odstranit** operátor na **to** ukazatel. [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md) vysvětluje, co se stane dále.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

