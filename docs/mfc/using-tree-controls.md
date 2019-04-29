---
title: Použití ovládacích prvků strom
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
ms.openlocfilehash: 9cff48018d728ef9578be38c0d94300011265fa1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411445"
---
# <a name="using-tree-controls"></a>Použití ovládacích prvků strom

Typické použití ovládacího prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) má následující tvar:

- Ovládací prvek je vytvořen. Pokud je ovládací prvek podle šablony dialogového okna, nebo pokud používáte `CTreeView`, vytvoření je automatická, když se vytvoří dialogové okno nebo zobrazení. Pokud chcete vytvořit stromu ovládacího prvku jako podřízeného okna ostatní okna, použijte [vytvořit](../mfc/reference/ctreectrl-class.md#create) členskou funkci.

- Pokud chcete vaše ovládacího prvku stromu, abyste mohli používat Image, nastavte seznam obrázků voláním [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Můžete také změnit odsazení voláním [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Je vhodná doba k tomu v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (pro ovládací prvky v dialogových oknech) nebo [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (pro zobrazení).

- Ukládat data do ovládacího prvku pomocí volání `CTreeCtrl`společnosti [metody InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkce jednou pro každou datovou položku. `InsertItem` Vrátí popisovač do položky, které vám umožní si ji později, třeba při přidání podřízené položky. Je vhodná doba k inicializaci dat v `OnInitDialog` (pro ovládací prvky v dialogových oknech) nebo `OnInitialUpdate` (pro zobrazení).

- Během interakce uživatele s ovládacím prvkem, odešle různé zprávy s oznámením. Můžete zadat funkce pro zpracování každé zprávy, které chcete zpracovat tak, že přidáte na on_notify_reflect – makro v mapování zprávy okno ovládacího prvku nebo tak, že přidáte ON_NOTIFY – makro mapování nadřazené okno zprávy. Zobrazit [zprávy s oznámením ovládacího prvku strom](../mfc/tree-control-notification-messages.md) dále v tomto tématu seznam možných oznámení.

- Volejte různé členské funkce Set k nastavení hodnot pro ovládací prvek. Změna, kterou můžete zahrnout nastavení odsazení a změně text, image nebo data související s položkou.

- Použijte různé funkce Get prozkoumat obsah ovládacího prvku. Můžete také procházet obsah ovládacího prvku stromu s funkcemi, které umožňují načtení popisovače nadřazené, podřízené položky a na stejné úrovni zadané položky. Dokonce můžete seřadit podřízené objekty daného konkrétní uzel.

- Jakmile budete hotovi s ovládacím prvkem, ujistěte se, že je správně zničeny. Pokud je ovládací prvek stromu v dialogovém okně, nebo pokud se jedná o zobrazení ho a `CTreeCtrl` bude objekt zničen. automaticky. Pokud ne, musíte zajistit, aby oba ovládací prvek a `CTreeCtrl` objektu jsou správně zničeny.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
