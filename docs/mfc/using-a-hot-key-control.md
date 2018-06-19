---
title: Použití ovládacího prvku klávesová zkratka | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4442d45cffdae63600fa3a405e29a139b149175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382941"
---
# <a name="using-a-hot-key-control"></a>Použití ovládacího prvku klávesová zkratka
Typické použití ovládacího prvku klávesová zkratka se následující níže:  
  
-   Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v poli šablony dialogového okna, je vytvoření automaticky při vytvoření dialogové okno. (Byste měli mít [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá za klíče ovládacího prvku.) Alternativně můžete použít [vytvořit](../mfc/reference/chotkeyctrl-class.md#create) – členská funkce vytvoření ovládacího prvku jako podřízeného okna časového období.  
  
-   Pokud chcete nastavit výchozí hodnotu pro ovládací prvek, zavolejte [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) – členská funkce. Pokud chcete zakázat určité stavy shift, zavolejte [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Pro ovládací prvky v dialogovém okně, je vhodná doba na k tomu v dialogových oken [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.  
  
-   Uživatel pracuje s ovládacím prvkem stisknutím kombinace kláves aktivní prvku aktivního klíče má. Uživatel pak nějakým způsobem označuje, že tato úloha je dokončena, možná kliknutím na tlačítko v dialogu.  
  
-   Pokud váš program je oznámeno, že uživatel vybral klávesové zkratky, měla by používat – členská funkce [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) načíst virtuální klíč a posunutí hodnoty stavu z ovládacího prvku aktivního klíče.  
  
-   Jakmile budete vědět, co klíče vybraného uživatele, můžete nastavit klávesové zkratky pomocí jedné z metod popsaných v [nastavení klávesové zkratky](../mfc/setting-a-hot-key.md).  
  
-   Pokud je aktivní klíče ovládací prvek v dialogovém okně, jeho a `CHotKeyCtrl` objektu budou automaticky zničena. Pokud ne, musíte zajistit, aby obě ovládacího prvku a `CHotKeyCtrl` objekt jsou správně zničena.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

