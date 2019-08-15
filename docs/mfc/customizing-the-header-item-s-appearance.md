---
title: Přizpůsobení vzhledu položky&#39;záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 6ce676695d717fcc5d418fe4ed5df91b4f9bca95
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508715"
---
# <a name="customizing-the-header-item39s-appearance"></a>Přizpůsobení vzhledu položky&#39;záhlaví

Nastavením parametru *dwStyle* při prvním vytvoření ovládacího prvku záhlaví ([CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create)) můžete definovat vzhled a chování položek záhlaví nebo samotného ovládacího prvku záhlaví.

Tady je vzorkování stylů, které můžete nastavit, a jejich účel:

- Aby položka hlavičky vypadala jako (pushbutton), použijte styl **HDS_BUTTONS** .

   Tento styl použijte v případě, že chcete provést akce v reakci na kliknutí myší na položku záhlaví, jako je například řazení dat podle konkrétního sloupce, jak je provedeno v aplikaci Microsoft Outlook.

- Chcete-li, aby záhlaví položky byly zobrazeny jako aktivní sledování, když na ně ukazatel myši projde, použijte styl **HDS_HOTTRACK** .

   Při sledování aktivního zobrazení se zobrazí 3D obrys jako ukazatel na položku v jiném nestrukturovaném pruhu.

- Pro indikaci, že by měl být ovládací prvek záhlaví skrytý, použijte styl **HDS_HIDDEN** .

   Styl **HDS_HIDDEN** označuje, že ovládací prvek záhlaví je určen pro použití jako datový kontejner, nikoli pro vizuální ovládací prvek. Tento styl automaticky neskrývá ovládací prvek, ale místo toho ovlivňuje chování `CHeaderCtrl::Layout`. Hodnota vrácená v `WINDOWPOS` členu *CY* struktury bude nulová, což znamená, že ovládací prvek by neměl být viditelný pro uživatele.

Další informace o těchto vlastnostech naleznete v tématu [položky](/windows/win32/Controls/header-controls) v Windows SDK. Informace o přidávání položek do ovládacího prvku záhlaví naleznete v tématu [Přidání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
