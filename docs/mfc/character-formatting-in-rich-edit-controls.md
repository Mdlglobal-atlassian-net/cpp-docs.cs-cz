---
title: "Formátování znaků v ovládacích prvcích pro úpravy s formátováním | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86b9686396d8f3bd6abd67f5a1f33be0d20bdc16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formátování znaků v ovládacích prvcích pro úpravy s formátováním
Můžete použít členské funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k formátování znaků a načíst informace o formátování. Znaky můžete zadat písmo, velikost, barvu a efekty například tučné, kurzíva a chráněné.  
  
 Můžete provést pomocí formátování znaků [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) a [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) členské funkce. Chcete-li zjistit aktuální znak formátování vybraného textu, použijte [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) – členská funkce. [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura s tyto členské funkce slouží k určení znaku atributy. Mezi důležité členů **CHARFORMAT** je **dwMask**. V `SetSelectionCharFormat` a `SetWordCharFormat`, **dwMask** Určuje atributy, které znak bude nastavena voláním této funkce. `GetSelectionCharFormat`sestavy atributy prvního znaku ve výběru; **dwMask** Určuje atributy, které jsou konzistentní v rámci výběr.  
  
 Můžete také získat a nastavit "výchozí formátování," tedy formátování, které se použijí na všechny následně vložené znaků. Například pokud aplikace nastaví výchozí znakovou formátování tučně a uživatel zadá poté znak, tento znak je tučně. K získání a nastavení výchozí formátování znaků, použijte [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) a [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) členské funkce.  
  
 Atribut "chráněné" znak nezmění vzhledu textu. Pokud se uživatel pokusí změnit chráněného textového, ovládacího prvku RichEdit odešle jeho nadřazeného okna **EN_PROTECTED** zprávy oznámení, povolení nadřazeného okna povolit nebo zakázat změny. Chybová zpráva oznámení, musíte povolit ho pomocí [seteventmask –](../mfc/reference/cricheditctrl-class.md#seteventmask) – členská funkce. Další informace o maska událostí najdete v tématu [oznámení z ovládacího prvku upravit bohaté](../mfc/notifications-from-a-rich-edit-control.md)dál v tomto tématu.  
  
 Barvu popředí je atribut znak, ale je vlastností ovládacího prvku RichEdit barvu pozadí. Pokud chcete nastavit barvu pozadí, použijte [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

