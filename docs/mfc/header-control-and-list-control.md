---
title: Ovládací prvky záhlaví a seznam
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370476"
---
# <a name="header-control-and-list-control"></a>Ovládací prvky záhlaví a seznam

Ve většině případů použijete ovládací prvek záhlaví, který je vložen do objektu [CListCtrl](../mfc/reference/clistctrl-class.md) nebo [CListView.](../mfc/reference/clistview-class.md) Existují však případy, kdy je žádoucí objekt ovládacího prvku samostatné záhlaví, jako je například manipulace s daty, uspořádané ve sloupcích nebo řádcích v objektu odvozeném [cview.](../mfc/reference/cview-class.md) V těchto případech budete potřebovat větší kontrolu nad vzhleda výchozí chování vložené záhlaví ovládacího prvku.

V běžném případě, že chcete záhlaví ovládací prvek poskytovat standardní, výchozí chování, můžete použít [CListCtrl](../mfc/reference/clistctrl-class.md) nebo [CListView](../mfc/reference/clistview-class.md) místo. Použijte, `CListCtrl` pokud chcete funkce výchozího ovládacího prvku záhlaví, vložené do seznamu zobrazit společný ovládací prvek. [CListView](../mfc/reference/clistview-class.md) použijte, pokud chcete funkce výchozího ovládacího prvku záhlaví, vložené do objektu zobrazení.

> [!NOTE]
> Tyto ovládací prvky zahrnují pouze integrovaný ovládací prvek záhlaví, pokud je ovládací prvek zobrazení seznamu vytvořen pomocí **stylu LVS_REPORT.**

Ve většině případů lze vzhled vloženého ovládacího prvku záhlaví změnit změnou stylů ovládacího prvku zobrazení obsahujícího seznamu. Kromě toho lze získat informace o ovládacím prvku záhlaví prostřednictvím členských funkcí ovládacího prvku zobrazení nadřazeného seznamu. Pro úplnou kontrolu a přístup k atributům a stylům vloženého ovládacího prvku záhlaví se však doporučuje získat ukazatel na objekt ovládacího prvku záhlaví.

Vložený objekt ovládacího prvku záhlaví `CListCtrl` lze `CListView` přistupovat z buď nebo `GetHeaderCtrl` s voláním členské funkce příslušné třídy. Následující kód ukazuje toto:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Použití seznamů obrázků s ovládacími prvky záhlaví](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
