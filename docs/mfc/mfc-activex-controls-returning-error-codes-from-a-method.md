---
title: 'MFC –ovládací prvky ActiveX: Vrácení chybových kódů z metody'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364539"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC –ovládací prvky ActiveX: Vrácení chybových kódů z metody

Tento článek popisuje, jak vrátit kódy chyb z metody ovládacího prvku ActiveX.

Chcete-li označit, že došlo k chybě v rámci metody, měli byste použít [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) členskou funkci, která bere SCODE (stavový kód) jako parametr. Můžete použít předdefinovaný SCODE nebo definovat jeden z vašich vlastních.

> [!NOTE]
> `ThrowError`je určen pouze jako prostředek vrácení chyby z funkce Get nebo Set vlastnosti nebo metody automatizace. Toto jsou pouze časy, které příslušné obslužné rutiny výjimky bude k dispozici v zásobníku.

Pomocné funkce existují pro nejběžnější předdefinované moduly SCONE, například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)a [COleControl::SetNotPovoleno](../mfc/reference/colecontrol-class.md#setnotpermitted).

Seznam předdefinovaných sconetů a pokyny k definování vlastních scones naleznete v části [Zpracování chyb v ovládacím prvku ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Rozšířená témata.

Další informace o vykazování výjimek v jiných oblastech kódu naleznete v [tématu COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [Zpracování chyb v ovládacím prvku ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Rozšířená témata.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
