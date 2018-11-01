---
title: Použití běžných ovládacích prvků v dialogovém okně
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: a17dac622ce1527a11d02888d6c4ce7905fcf669
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458647"
---
# <a name="using-common-controls-in-a-dialog-box"></a>Použití běžných ovládacích prvků v dialogovém okně

Běžné ovládací prvky Windows lze použít v [dialogových oknech](../mfc/dialog-boxes.md), formuláře, zobrazení, zobrazení záznamů a žádné jiné okno založen na šabloně dialogu. Následující postup s menšími změnami, budou fungovat i formulářů.

## <a name="procedures"></a>Procedury

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Použití běžného ovládacího prvku v dialogovém okně

1. Umístit ovládací prvek v šabloně dialogu [použití editoru dialogových oken](../mfc/using-the-dialog-editor-to-add-controls.md).

1. Přidejte do třídy dialogového okna členskou proměnnou, která představuje ovládací prvek. V **přidat členskou proměnnou** dialogu zaškrtněte políčko **řídicí proměnná** a ujistěte se, že **ovládací prvek** vybraná **kategorie**.

1. Pokud tento běžný ovládací prvek poskytuje vstup do programu, deklarujte dalšího člena variable(s) ve třídě dialog pro zpracování jsou vstupní hodnoty.

    > [!NOTE]
    >  Můžete přidat tyto členské proměnné pomocí místní nabídky v zobrazení tříd (viz [přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) pro vlastní třídy dialogového okna, nastavte počáteční podmínky pro běžný ovládací prvek. Členské funkce pomocí členské proměnné, vytvořené v předchozím kroku, použijte k nastavení výchozí hodnoty a další nastavení. Následující popisy ovládacích prvků pro podrobnosti naleznete na nastavení.

   Můžete také použít [výměna dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md) (DDX) k inicializaci ovládacích prvků v dialogovém okně.

1. V obslužné rutiny pro ovládací prvky v dialogovém okně manipulovat s prvkem pomocí členské proměnné. Najdete v následujících popisech ovládací prvky pro podrobnosti pro metody.

    > [!NOTE]
    >  Členské proměnné budou existovat jenom jako dialogové okno samotné existuje. Nebudete mít k dotazování ovládacího prvku pro zadávání hodnot po zavření dialogových oken. Chcete-li pracovat s vstupní hodnoty z běžného ovládacího prvku, přepište `OnOK` ve vlastní třídy dialogového okna. V přepsání dotaz ovládacího prvku pro zadávání hodnot a uložte tyto hodnoty členské proměnné třídy dialogového okna.

    > [!NOTE]
    >  Výměna dat dialogových oken můžete také použít k nastavení nebo načtení hodnoty z ovládacích prvků v dialogovém okně.

## <a name="remarks"></a>Poznámky

Přidání některých běžných ovládacích prvků do dialogového okna způsobí, že dialogových oken přestane fungovat. Odkazovat na [dialogové okno Přidání ovládacích prvků dialogového okna způsobí, že se funkce již](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) pro další informace o zpracování této situaci.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat

- [Přidání ovládacích prvků do dialogového okna ručně místo pomocí editoru dialogových oken](../mfc/adding-controls-by-hand.md)

- [Ovládací prvek odvození od některého ze standardních běžné ovládací prvky Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Použití běžného ovládacího prvku jako podřízeného okna](../mfc/using-a-common-control-as-a-child-window.md)

- [Příjem oznámení z ovládacího prvku](../mfc/receiving-notification-from-common-controls.md)

- [Použít výměna dat dialogových oken (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>Viz také

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

