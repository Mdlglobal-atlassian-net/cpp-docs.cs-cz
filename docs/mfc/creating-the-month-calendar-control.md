---
title: Vytvoření ovládacího prvku měsíční kalendář
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: f98ce6c0272b64442d42cb0ba78b10affe5ede8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523768"
---
# <a name="creating-the-month-calendar-control"></a>Vytvoření ovládacího prvku měsíční kalendář

Jak vytvořit ovládací prvek měsíční kalendář závisí na, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo jeho vytváření v okně nondialog.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Použití atributu CMonthCalCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidáte do šablony prostředku dialogového okna Ovládací prvek měsíční kalendář. Zadejte své ID ovládacího prvku.

1. Zadejte všechny styly potřeby pomocí dialogového okna vlastnosti z ovládací prvek měsíční kalendář.

1. Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidat členskou proměnnou typu [atributu CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) s vlastností ovládacího prvku. Tento člen můžete použít k volání `CMonthCalCtrl` členské funkce.

1. Použití mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládacího prvku kalendáře měsíce zprávy v okně Vlastnosti potřeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavte pro všechny další styly `CMonthCalCtrl` objektu.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>V okně nondialog použití atributu CMonthCalCtrl

1. Definování ovládacího prvku ve třídě zobrazení nebo okno.

1. Volání ovládacího prvku [vytvořit](../mfc/reference/cmonthcalctrl-class.md#create) členské funkce, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), může být co nejdříve jako nadřazené okno [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkci obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.

## <a name="see-also"></a>Viz také

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

