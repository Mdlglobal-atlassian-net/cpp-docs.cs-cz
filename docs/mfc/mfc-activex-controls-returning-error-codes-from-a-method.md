---
title: 'MFC – ovládací prvky ActiveX: Vrácení chybových kódů z metody'
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
ms.openlocfilehash: 0800c1827c636dd81e2928e33c0ee2afde4c94ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324269"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC – ovládací prvky ActiveX: Vrácení chybových kódů z metody

Tento článek popisuje, jak vrátit kódy chyb z metody ovládacího prvku ActiveX.

K označení, že v rámci metody došlo k chybě, byste měli použít [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) členskou funkci, která přebírá SCODE (stavový kód) jako parametr. Můžete použít předdefinované SCODE nebo definovat svůj vlastní.

> [!NOTE]
>  `ThrowError` je určen pro použití pouze jako způsob vrátit chybu z v rámci vlastnosti Get nebo Set funkce nebo metoda služby automation. Jedná se o jediný případů, kdy se obslužná rutina příslušné výjimky budou k dispozici v zásobníku.

Neexistuje pomocné funkce, nejběžnější předdefinované SCODEs, jako například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), a [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Seznam předdefinovaných SCODEs a pokyny k definování vlastní SCODEs, najdete v části [zpracování chyb v svůj ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Pokročilá témata.

Další informace o vytváření sestav výjimky v jiných oblastech, které váš kód, naleznete v tématu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [zpracování chyb v svůj ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Pokročilá témata.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
