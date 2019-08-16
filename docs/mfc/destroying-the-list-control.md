---
title: Likvidace ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 5004026da6bb309cc2c966384724b7b98e254e1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508708"
---
# <a name="destroying-the-list-control"></a>Likvidace ovládacího prvku seznam

Pokud vložíte objekt [CListCtrl](../mfc/reference/clistctrl-class.md) jako datový člen třídy zobrazení nebo dialogového okna, je zničena, když je jeho vlastník zničen. Použijete-li [CListView –](../mfc/reference/clistview-class.md), rozhraní zničí ovládací prvek při zničení zobrazení.

Pokud seřadíte některé z vašich dat seznamu, aby byly uloženy v aplikaci, nikoli v ovládacím prvku seznam, bude nutné pro své zrušení přidělit. Další informace naleznete v tématu [položky zpětného volání a maska zpětného volání](/windows/win32/Controls/using-list-view-controls) v Windows SDK.

Kromě toho zodpovídáte za zrušení přidělení všech seznamů obrázků, které jste vytvořili a přidružili k objektu ovládacího prvku seznam.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
