---
title: Položky zpětného volání a maska zpětného volání
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 5c326d8498ea297936254a8650f666103ea3c772
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509134"
---
# <a name="callback-items-and-the-callback-mask"></a>Položky zpětného volání a maska zpětného volání

Pro každou z jeho položek ovládací prvek zobrazení seznamu obvykle ukládá text popisku, index seznamu obrázků ikon položky a sadu bitových příznaků pro stav položky. Můžete definovat jednotlivé položky jako položky zpětného volání, které jsou užitečné, pokud aplikace již ukládá některé informace pro položku.

Můžete definovat položku jako položku zpětného volání zadáním příslušných hodnot pro `pszText` členy `LVITEM` a `iImage` struktury (viz [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)). Pokud aplikace udržuje text položky nebo podpoložky, zadejte hodnotu **LPSTR_TEXTCALLBACK** pro `pszText` člena. Pokud aplikace sleduje ikonu pro položku, zadejte hodnotu **I_IMAGECALLBACK** pro `iImage` člena.

Kromě definování položek zpětného volání můžete také upravit masku zpětného volání ovládacího prvku. Tato maska je sada bitových příznaků, které určují stavy položek, pro které aplikace místo ovládacího prvku ukládá aktuální data. Maska zpětného volání se vztahuje na všechny položky ovládacího prvku na rozdíl od označení položky zpětného volání, které se vztahuje na konkrétní položku. Maska zpětného volání má ve výchozím nastavení hodnotu nula, což znamená, že ovládací prvek sleduje všechny stavy položek. Chcete-li změnit toto výchozí chování, inicializujte masku na libovolnou kombinaci následujících hodnot:

- **LVIS_CUT** Položka je označena pro operaci vyjmutí a vložení.

- **LVIS_DROPHILITED** Položka je zvýrazněna jako cíl přetažení myší.

- **LVIS_FOCUSED** Položka má fokus.

- **LVIS_SELECTED** Je vybrána položka.

- **LVIS_OVERLAYMASK** Aplikace ukládá index seznamu obrázků aktuálního překrytí obrázku pro každou položku.

- **LVIS_STATEIMAGEMASK** Aplikace ukládá index seznamu obrázků aktuálního stavu pro každou položku.

Další informace o načtení a nastavení této masky naleznete v tématu [CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) a [CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
