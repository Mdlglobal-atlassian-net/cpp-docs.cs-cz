---
title: Položky zpětného volání a maska zpětného volání
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 35967f128c6cc59bc9cea90da559b32c51fb38d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261073"
---
# <a name="callback-items-and-the-callback-mask"></a>Položky zpětného volání a maska zpětného volání

Pro každou z položek ovládací prvek zobrazení seznamu obvykle ukládá text popisku, index bitové kopie seznamu ikon položky a sadu bitové příznaky pro položky stavu. Jednotlivé položky můžete definovat jako položky zpětného volání, které jsou užitečné, pokud už vaše aplikace ukládá některé informace pro položku.

Definujte položku jako položka zpětného volání tak, že zadáte odpovídající hodnoty pro `pszText` a `iImage` členy **LV_ITEM** strukturu (naleznete v tématu [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem)). Pokud aplikace udržuje položky nebo podřízenou položku v textu, zadejte **LPSTR_TEXTCALLBACK** hodnota `pszText` člena. Pokud na ikonu pro položku uchovává informace o aplikaci, zadejte **I_IMAGECALLBACK** hodnota `iImage` člena.

Kromě definování položky zpětného volání, můžete také upravit maska zpětného volání ovládacího prvku. Tato maska je sadu bitových příznaků, které určují stavy položky, pro které aplikace, spíše než ovládací prvek, uloží aktuální data. Maska zpětného volání se vztahuje na všechny položky ovládacího prvku, na rozdíl od označení položka zpětného volání, která se vztahuje k určité položce. Maska zpětného volání je nula ve výchozím nastavení, což znamená, že ovládací prvek sleduje všechny stavy položky. Chcete-li změnit toto výchozí chování, inicializujte maska pro libovolnou kombinaci následujícího:

- **LVIS_CUT** položky je označen pro operace vyjmutí a vložení.

- **LVIS_DROPHILITED** položky se zvýrazní jako cíl přetažení myší.

- **LVIS_FOCUSED** položka má fokus.

- **LVIS_SELECTED** výběru položky.

- **LVIS_OVERLAYMASK** ale aplikace ukládá seznam index bitové kopie aktuální Image překrytí pro každou položku.

- **LVIS_STATEIMAGEMASK** ale aplikace ukládá seznam index bitové kopie aktuální stav obrázku pro každou položku.

Další informace o načtení a nastavení masky najdete v tématu [CListCtrl::GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) a [CListCtrl::SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
