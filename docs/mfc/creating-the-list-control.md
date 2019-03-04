---
title: Vytvoření ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: 7b2cb47699339dd413dc1bfae7623069da56e7a4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303643"
---
# <a name="creating-the-list-control"></a>Vytvoření ovládacího prvku seznam

Jak řídit seznamu ([CListCtrl](../mfc/reference/clistctrl-class.md)) se vytvoří závisí na tom, jestli jste pomocí ovládacího prvku přímo nebo horizontálních oddílů pomocí třídy [CListView](../mfc/reference/clistview-class.md) místo. Pokud používáte `CListView`, rozhraní vytvoří zobrazení jako součást jeho pořadí vytváření dokumentů/zobrazení. Vytváření zobrazení seznamu vytvoří ovládací prvek seznamu také (dvě se stejnou věc). Ovládací prvek je vytvořen v zobrazení [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkci obslužné rutiny. V tomto případě je připravené k přidání položek prostřednictvím volání do ovládacího prvku [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Použití třídy CListCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidáte do šablony prostředku dialogového okna ovládacího prvku seznamu. Zadejte své ID ovládacího prvku.

1. Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidat členskou proměnnou typu `CListCtrl` s vlastností ovládacího prvku. Tento člen můžete použít k volání `CListCtrl` členské funkce.

1. Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládacího prvku seznam zpráv je potřeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení stylů pro `CListCtrl`. Zobrazit [změna stylů ovládacího prvku seznamu](../mfc/changing-list-control-styles.md). Určuje druh "Zobrazit" se zobrazí v ovládacím prvku, i když můžete později změnit zobrazení.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>V okně nondialog použití třídy CListCtrl

1. Definování ovládacího prvku ve třídě zobrazení nebo okno.

1. Volání ovládacího prvku [vytvořit](../mfc/reference/clistctrl-class.md#create) členské funkce, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), může být co nejdříve jako nadřazené okno [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkci obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
