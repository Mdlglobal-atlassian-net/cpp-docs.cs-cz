---
title: Zpracování zpráv s oznámením v ovládacím prvku matrice
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 948990c8597c2ccdcec496252c6801c02a78cbf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507962"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Zpracování zpráv s oznámením v ovládacím prvku matrice

V nadřazené třídě ovládacího prvku matrice vytvořte `OnChildNotify` funkci obslužné rutiny s příkazem Switch pro jakékoli oznamovací zprávy matrice (`CReBarCtrl`), které chcete zpracovat. Oznámení se odesílají do nadřazeného okna, když uživatel přetáhne objekty přes ovládací prvek matrice, změní rozložení matrice pásma, odstraní pruhy z ovládacího prvku matrice a tak dále.

Následující zprávy oznámení lze odeslat pomocí objektu ovládacího prvku matrice:

- RBN_AUTOSIZE odesílá matrice ovládacímu prvku (vytvořenému ve stylu RBS_AUTOSIZE), když se matrice automaticky změní.

- RBN_BEGINDRAG odesílá ovládacímu prvku matrice, když uživatel začne přetahovat do pásma.

- RBN_CHILDSIZE odesílá ovládacímu prvku matrice při změně velikosti podřízeného okna pásma.

- RBN_DELETEDBAND odesílá ovládacímu prvku matrice po odstranění pásma.

- RBN_DELETINGBAND odesílá ovládacímu prvku matrice při odstraňování pásma.

- RBN_ENDDRAG odesílá ovládacímu prvku matrice, když uživatel přestává přetahováním pásma.

- RBN_GETOBJECT odesílá matrice ovládacímu prvku (vytvořenému ve stylu RBS_REGISTERDROP), když se objekt přetáhne přes pásmo v ovládacím prvku.

- RBN_HEIGHTCHANGE odesílá ovládací prvek matrice, když se změní jeho výška.

- RBN_LAYOUTCHANGED odesílá ovládacímu prvku matrice, když uživatel změní rozložení pásem ovládacího prvku.

Další informace o těchto oznámeních naleznete v tématu [reference ovládacího prvku matrice](/windows/win32/controls/rebar-control-reference) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
