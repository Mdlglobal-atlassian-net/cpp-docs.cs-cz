---
title: Vytvoření ovládacího prvku karta
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: c444c938c88c2e8bf079f0f3eba80776c54af5ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573404"
---
# <a name="creating-the-tab-control"></a>Vytvoření ovládacího prvku karta

Vytvoření ovládacího prvku karta závisí na tom, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo vytváří v okně nondialog.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Použití atributu CTabCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidáte do šablony prostředku dialogového okna ovládacího prvku karta. Zadejte své ID ovládacího prvku.

1. Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidat členskou proměnnou typu [atributu CTabCtrl](../mfc/reference/ctabctrl-class.md) s vlastností ovládacího prvku. Tento člen můžete použít k volání `CTabCtrl` členské funkce.

1. Mapování funkce obslužné rutiny ve třídě dialog pro všechny zprávy oznámení ovládacího prvku karty, které je potřeba zpracovat. Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení stylů pro `CTabCtrl`.

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>V okně nondialog použití atributu CTabCtrl

1. Definování ovládacího prvku ve třídě zobrazení nebo okno.

1. Volání ovládacího prvku [vytvořit](../mfc/reference/ctabctrl-class.md#create) členské funkce, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), může být co nejdříve jako nadřazené okno [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkci obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.

Po `CTabCtrl` objekt byl vytvořen, můžete nastavit nebo zrušte tyto rozšířené styly:

- **Tcs_ex_flatseparators –** ovládacího prvku karta nakreslí oddělovače mezi položkami kartu. Rozšířený styl pouze kartu ovládací prvky, které mají vliv **TCS_BUTTONS** a **TCS_FLATBUTTONS** styly. Ve výchozím nastavení, vytvoření ovládacího prvku karta s **TCS_FLATBUTTONS** styl nastaví tento rozšířený styl.

- **Tcs_ex_registerdrop –** ovládacího prvku karta generuje **TCN_GETOBJECT** zpráv s oznámením o cíle přetažení objektu, když je objekt přetažen přes kartu položek v ovládacím prvku.

    > [!NOTE]
    >  Pro příjem **TCN_GETOBJECT** oznámení, je třeba inicializovat knihovny OLE voláním [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

Dají se tyto styly načíst a nastavit, po vytvoření ovládacího prvku pomocí odpovídajících volání [GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) a [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) členské funkce.

Například nastavit **tcs_ex_flatseparators –** style s následujícími řádky kódu:

[!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]

Zrušte **tcs_ex_flatseparators –** stylu z `CTabCtrl` objektu s následujícími řádky kódu:

[!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]

Tato akce odebere oddělovače, které se zobrazí mezi tlačítek vaše `CTabCtrl` objektu.

## <a name="see-also"></a>Viz také

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

