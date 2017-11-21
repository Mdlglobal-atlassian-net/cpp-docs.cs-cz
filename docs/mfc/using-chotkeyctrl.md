---
title: "Používání atributu CHotKeyCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CHotKeyCtrl
dev_langs: C++
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a4cb304e014412e16f425b4162fd4950dcc7789f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

