---
title: Atributy pro řízení karty a karta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd2129ad4b2dc075893a730c0ba75de96dbebea0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952856"
---
# <a name="tabs-and-tab-control-attributes"></a>Karty a atributy ovládacího prvku karta
Máte značnou ovládat vzhled a chování karet, které tvoří ovládacího prvku karta ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Každé kartě může mít štítek, ikonu, v položce stavu a s ním spojená hodnotu 32-bit definované aplikací. Pro každé kartě můžete zobrazit ikona, popisek nebo obojí.  
  
 Kromě toho každá položka karta může mít tři možné stavy: stisknutí, stavů nebo zvýraznit. Tento stav lze nastavit pouze úpravou existující položky kartě. Pokud chcete upravit existující položky kartě, načíst pomocí volání [GetItem](../mfc/reference/ctabctrl-class.md#getitem), upravit `TCITEM` struktury (konkrétně *dwState* a *dwStateMask* datové členy ) a pak se vraťte upravené `TCITEM` struktura s volání [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Pokud je nutné vymazat stavy položek všechny karty položek v `CTabCtrl` objektu, ujistěte se, volání [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Tato funkce obnoví stav všechny položky kartě nebo všechny položky s výjimkou toho, které jsou aktuálně vybrané.  
  
 Následující kód vymaže stav všechny karty položky a poté změní stav třetí položky:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]  
  
 Další informace o kartě atributy najdete v tématu [karty a atributy karta](http://msdn.microsoft.com/library/windows/desktop/bb760550) ve Windows SDK. Další informace o přidání karet do ovládacího prvku karta najdete v tématu [přidání karet do ovládacího prvku karta](../mfc/adding-tabs-to-a-tab-control.md) dál v tomto tématu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

