---
title: "Aktuální výběr v ovládacím prvku pro úpravy s formátováním | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b41b99ca515cb91c097cb20c3ef0cd0e5dccb64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="current-selection-in-a-rich-edit-control"></a>Aktuální výběr v ovládacích prvcích pro úpravy s formátováním
Uživatele můžete vybrat text v ovládacím prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pomocí myši nebo klávesnice. Aktuální výběr je rozsah vybrané znaky nebo jsou vybrané pozice kurzoru, pokud se žádné znaky. Aplikaci můžete získat informace o aktuálním výběrem, nastavit aktuální výběr, určit, kdy aktuální výběr změny a zobrazit nebo skrýt výběr zvýrazněte.  
  
 Chcete-li zjistit aktuální výběr v ovládacím prvku RichEdit, použijte [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) – členská funkce. Pokud chcete nastavit aktuální výběr, použijte [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) – členská funkce. [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura s tyto funkce slouží k určení rozsah znaků. Pokud chcete načíst informace o obsahu aktuální výběr, můžete použít [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) – členská funkce.  
  
 Ve výchozím nastavení ovládacího prvku RichEdit ukazuje a skryje zvýraznění výběr při získá a již není vybrán. Můžete zobrazit nebo skrýt výběr zvýraznění kdykoli pomocí [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) – členská funkce. Aplikace může například zadat dialogové okno hledání najít text v ovládacím prvku RichEdit. Aplikace může vyberte text, odpovídající bez zavření dialogového okna, v takovém případě musíte použít `HideSelection` zvýrazněte výběr.  
  
 Zobrazí vybraný text v ovládacím prvku RichEdit, použijte [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) – členská funkce. Text je zkopírován do zadané pole znaků. Je nutné zajistit, že je pole dostatečně velký pro uložení vybraného textu plus ukončující znak hodnoty null.  
  
 Můžete hledat řetězec v ovládacím prvku RichEdit pomocí [řetězec FindText](../mfc/reference/cricheditctrl-class.md#findtext) – členská funkce [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) struktura používaná pomocí této funkce určuje rozsah text a hledaný řetězec pro hledání. Tyto možnosti můžete zadat taky jako jestli hledání je malá a velká písmena.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

