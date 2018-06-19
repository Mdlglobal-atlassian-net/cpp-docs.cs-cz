---
title: Používání atributu CHotKeyCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CHotKeyCtrl
dev_langs:
- C++
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3678d95ff0748c1854e509d898dfa89778c9a5f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381800"
---
# <a name="using-chotkeyctrl"></a>Používání atributu CHotKeyCtrl
Ovládacího prvku klávesová zkratka, reprezentována třída [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), je okno, které zobrazí textové reprezentace kombinace kláves uživatel zadá do ní, jako je například CTRL + SHIFT + Q. Také udržuje interního vyjádření tohoto klíče ve formuláři virtuální klíče kódu a sadu příznaky, které představují shift stavu. Ovládací prvek aktivního klíče ve skutečnosti nenastaví klávesové zkratky – učinit je váš program. (Seznam kódů standardní virtuální klíčů najdete v tématu winuser.)  
  
 Použití ovládacího prvku klávesová zkratka k získání vstupu uživatele, pro které klávesové zkratky pro přidružení k okno nebo přístup z více vláken. Ovládací prvky klávesových zkratek se často používají v dialogových oknech, například může zobrazit při žádosti o přiřadit klávesové zkratky. Je váš program odpovědností načíst hodnoty popisující klávesové zkratky z ovládacího prvku aktivního klíče a volat příslušná funkce pro přidružení klávesové zkratky okno nebo přístup z více vláken.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Použití ovládacího prvku klávesová zkratka](../mfc/using-a-hot-key-control.md)  
  
-   [Nastavení klávesové zkratky](../mfc/setting-a-hot-key.md)  
  
-   [Globální klávesové zkratky](../mfc/global-hot-keys.md)  
  
-   [Klávesové zkratky specifické pro vlákno](../mfc/thread-specific-hot-keys.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../mfc/controls-mfc.md)

