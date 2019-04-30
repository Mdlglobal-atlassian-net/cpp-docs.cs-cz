---
title: Zpracování zpráv s oznámením v ovládacím prvku matrice
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 8ac225802bd1d0a0a4b0f30e017fa677f1072fd3
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339624"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Zpracování zpráv s oznámením v ovládacím prvku matrice

V nadřazené třídě ovládacího prvku matrice, vytvořte `OnChildNotify` funkci obslužné rutiny pomocí příkazu switch pro libovolný matrice – ovládací prvek (`CReBarCtrl`) zpracování zpráv s oznámením. Oznámení se posílají nadřazenému oknu, když uživatel přetáhne objekty nad ovládacím prvkem matrice, změny rozložení pruhy matrice, odstraní pásmech z ovládacího prvku matrice a tak dále.

Objekt ovládacího prvku matrice může odeslat následující upozornění:

- RBN_AUTOSIZE odesílaných ovládacím prvkem matrice (vytvořenou pomocí stylu RBS_AUTOSIZE) Pokud matrice automaticky změní velikost sebe sama.

- RBN_BEGINDRAG odesílaných ovládacího prvku rebar, když uživatel zahájí přetahování pásmo.

- RBN_CHILDSIZE odesílaných ovládacím prvkem matrice při změně velikosti podřízeného okna.

- RBN_DELETEDBAND odesílaných ovládacím prvkem matrice po odstranění svazku.

- RBN_DELETINGBAND odesílaných ovládacím prvkem matrice pásmo se neodstraní.

- RBN_ENDDRAG odesílaných ovládacího prvku rebar, když uživatel přestane přetahovat pásmo.

- RBN_GETOBJECT odesílaných ovládacím prvkem matrice (vytvořenou pomocí stylu RBS_REGISTERDROP) když je objekt přetažen přes vzdálené správy v rámci ovládacího prvku.

- RBN_HEIGHTCHANGE odesílaných ovládacího prvku rebar, když došlo ke změně jeho výška.

- RBN_LAYOUTCHANGED odesílaných ovládacího prvku rebar, když uživatel změní rozložení pásem ovládacího prvku.

Další informace o těchto oznámeních najdete v tématu [matrice – ovládací prvek odkazu](/windows/desktop/controls/rebar-control-reference) v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
