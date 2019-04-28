---
title: Ovládací prvek seznamu a zobrazení seznamu
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: 5c9612a22eab27d568c0dbb86d29ba031fe5985e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365324"
---
# <a name="list-control-and-list-view"></a>Ovládací prvek seznamu a zobrazení seznamu

Pro usnadnění práce knihovny MFC zapouzdřuje ovládacího prvku seznam dvěma způsoby. Můžete použít ovládací prvky seznamu:

- Přímo, s využitím vkládání služby [CListCtrl](../mfc/reference/clistctrl-class.md) objekt ve třídě dialog.

- Nepřímo pomocí třídy [CListView](../mfc/reference/clistview-class.md).

`CListView` umožňuje snadno integrovat ovládací prvek seznamu architekturu document/view knihovny MFC, zapouzdření ovládací prvek velká jako [CEditView](../mfc/reference/ceditview-class.md) zapouzdřuje ovládacího prvku pro úpravy: ovládací prvek vyplní celou oblast povrchu zobrazení MFC. (Zobrazení *je* ovládací přetypovat na `CListView`.)

A `CListView` objekt dědí z [cctrlview –](../mfc/reference/cctrlview-class.md) a její základní třídy a přidá členskou funkci načíst základní ovládací prvek seznamu. Zobrazit členy použijte pro práci se zobrazením v zobrazení. Použití [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) členskou funkci získat přístup k členské funkce ovládacího prvku seznamu. Pomocí těchto členů na:

- Přidat, odstranit nebo manipulaci s "položky" v seznamu.

- Nastavit nebo získat atributy ovládacího prvku seznamu.

K získání odkazu na `CListCtrl` základní `CListView`, volání `GetListCtrl` z vaší třídy zobrazení seznamu:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

Toto téma popisuje oba způsoby, jak pomocí ovládacího prvku seznamu.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
