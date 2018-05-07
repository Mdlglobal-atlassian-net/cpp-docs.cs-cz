---
title: Zprávy s oznámením posuvníku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b003e23a1fef2b44600b9fd15dfe4ca541df5369
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="slider-notification-messages"></a>Zprávy s oznámením pro posuvník
Ovládací prvek typu jezdec upozorní jeho nadřazeného okna akcí uživatele zasláním nadřazené `WM_HSCROLL` nebo `WM_VSCROLL` zprávy, v závislosti na orientaci posuvníku. Chcete-li zpracovat tyto zprávy, přidejte obslužné rutiny pro `WM_HSCROLL` a `WM_VSCROLL` zprávy do nadřazeného okna. [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) a [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) členské funkce se předají kód oznámení, pozice posuvníku a odkazy [CSliderCtrl](../mfc/reference/csliderctrl-class.md) objektu. Všimněte si, že je ukazatel typu **CScrollBar \***  to i v případě, že odkazuje `CSliderCtrl` objektu. Budete muset přiřazení tento ukazatel typu, pokud budete potřebovat k manipulaci s posuvníku.  
  
 Ovládací prvky posuvníku místo pomocí posuvník oznámení kódy, odeslání jinou sadu kódy upozornění. Odešle ovládací prvek typu jezdec **TB_BOTTOM**, **TB_LINEDOWN**, **TB_LINEUP**, a **TB_TOP** oznámení kódy jenom v případě, že uživatel pracuje s ovládací prvek typu jezdec pomocí klávesnice. **TB_THUMBPOSITION** a **TB_THUMBTRACK** zprávy oznámení se odesílají jenom při uživatele je pomocí myši. **TB_ENDTRACK**, **TB_PAGEDOWN**, a **TB_PAGEUP** kódy oznámení se odesílají v obou případech.  
  
 Následující tabulka uvádí zprávy s oznámením ovládacího prvku posuvník a událostí (virtuální klíče kódy nebo události myši), které způsobí oznámení k odeslání. (Seznam kódů standardní virtuální klíčů najdete v tématu winuser.)  
  
|Zpráva upozornění|Události, která způsobila oznámení k odeslání|  
|--------------------------|-------------------------------------------|  
|**TB_BOTTOM**|**VK_END**|  
|**TB_ENDTRACK**|`WM_KEYUP` (uživatel vydané klíč, který odeslal relevantní virtuální klíče kód)|  
|**TB_LINEDOWN**|**VK_RIGHT** nebo **VK_DOWN**|  
|**TB_LINEUP**|**VK_LEFT** nebo **VK_UP**|  
|**TB_PAGEDOWN**|**VK_NEXT** (uživatel klepl kanál pod nebo napravo od jezdce.)|  
|**TB_PAGEUP**|**VK_PRIOR** (uživatel klepl kanál nad nebo nalevo od jezdce.)|  
|**TB_THUMBPOSITION**|`WM_LBUTTONUP` Následující **TB_THUMBTRACK** oznámení|  
|**TB_THUMBTRACK**|Přesun posuvník (uživatel přetažením jezdec)|  
|**TB_TOP**|**VK_HOME**|  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

