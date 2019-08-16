---
title: Styly ovládacího prvku strom
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510934"
---
# <a name="tree-control-styles"></a>Styly ovládacího prvku strom

Styly ovládacího prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) určují aspekty vzhledu ovládacího prvku stromu. Počáteční styly nastavíte při vytváření ovládacího prvku strom. Styly můžete načíst a změnit po vytvoření ovládacího prvku stromu pomocí funkcí Windows [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) a [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) a zadáním **GWL_STYLE** pro parametr *nIndex* . Úplný seznam stylů naleznete v tématu [styly oken ovládacího prvku stromového zobrazení](/windows/win32/Controls/tree-view-control-window-styles) v Windows SDK.

Styl **TVS_HASLINES** vylepšuje grafické znázornění hierarchie ovládacího prvku stromu kreslením čar, které propojují podřízené položky s odpovídající nadřazenou položkou. Tento styl neodkazuje na položky v kořenu hierarchie. K tomu je třeba kombinovat styly **TVS_HASLINES** a **TVS_LINESATROOT** .

Uživatel může rozbalit nebo sbalit seznam podřízených položek nadřazené položky dvojitým kliknutím na nadřazenou položku. Ovládací prvek stromu, který má styl **TVS_SINGLEEXPAND** , způsobí, že položka je vybrána pro rozšíření, a položka, která je vybrána k sbalení. Pokud se myš používá k výběru vybrané položky jedním kliknutím a tato položka je zavřená, rozšíří se. Pokud je vybraná položka po otevření otevřená jen jednou, bude sbalená.

Strom ovládacího prvku, který má styl **TVS_HASBUTTONS** , přidá tlačítko na levou stranu každé nadřazené položky. Uživatel může kliknout na tlačítko a rozbalit nebo sbalit podřízené položky jako alternativu pro poklikání na nadřazenou položku. **TVS_HASBUTTONS** nepřidává tlačítka do položek v kořenu hierarchie. K tomu je třeba kombinovat **TVS_HASLINES**, **TVS_LINESATROOT**a **TVS_HASBUTTONS**.

Styl **TVS_EDITLABELS** umožňuje uživateli upravit popisky položek ovládacího prvku stromové struktury. Další informace o úpravách popisků naleznete v tématu [úprava popisku ovládacího prvku strom](../mfc/tree-control-label-editing.md) dále v tomto tématu.

Styl **TVS_NOTOOLTIPS** zakáže automatickou funkci tipu nástroje v ovládacích prvcích stromového zobrazení. Tato funkce automaticky zobrazí popis tlačítka, který obsahuje název položky pod kurzorem myši, pokud celý nadpis není aktuálně zobrazen.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
