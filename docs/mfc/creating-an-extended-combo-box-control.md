---
title: Vytvoření ovládacího prvku rozšířené pole se seznamem
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: d1e81664403f45a0a35cd24ceea16e1425b03403
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668764"
---
# <a name="creating-an-extended-combo-box-control"></a>Vytvoření ovládacího prvku rozšířené pole se seznamem

Vytvoření ovládacího prvku rozšířené pole se seznamem pole závisí na, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo jeho vytváření v okně nondialog.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Použití atributu CComboBoxEx přímo v dialogovém okně

1. V editoru dialogového okna přidáte do šablony prostředku dialogového okna ovládacího prvku rozšířené pole se seznamem. Zadejte své ID ovládacího prvku.

1. Zadejte všechny styly potřeby pomocí dialogového okna vlastnosti ovládacího prvku rozšířené pole se seznamem.

1. Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidat členskou proměnnou typu [atributu CComboBoxEx](../mfc/reference/ccomboboxex-class.md) s vlastností ovládacího prvku. Tento člen můžete použít k volání `CComboBoxEx` členské funkce.

1. Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog potřebujete zpracovávat zprávy oznámení ovládacího prvku rozšířené pole se seznamem pole (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavte pro všechny další styly `CComboBoxEx` objektu.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>V okně nondialog použití atributu CComboBoxEx

1. Definování ovládacího prvku ve třídě zobrazení nebo okno.

1. Volání ovládacího prvku [vytvořit](../mfc/reference/ctabctrl-class.md#create) členské funkce, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), může být co nejdříve jako nadřazené okno [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkci obslužné rutiny. Nastavení stylů pro ovládací prvek.

## <a name="see-also"></a>Viz také

[Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

