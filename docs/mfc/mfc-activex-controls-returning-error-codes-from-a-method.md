---
title: 'MFC – ovládací prvky ActiveX: Vrácení chybových kódů z metody | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaa86f6f57d28b56a7374ff64b0fcbca2a3d98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383594"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC –ovládací prvky ActiveX: Vrácení chybových kódů z metody

Tento článek popisuje, jak vrátit kódy chyb z metody ovládacího prvku ActiveX.

K označení, že v rámci metody došlo k chybě, byste měli použít [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) členskou funkci, která přebírá SCODE (stavový kód) jako parametr. Můžete použít předdefinované SCODE nebo definovat svůj vlastní.

> [!NOTE]
>  `ThrowError` je určen pro použití pouze jako způsob vrátit chybu z v rámci vlastnosti Get nebo Set funkce nebo metoda služby automation. Jedná se o jediný případů, kdy se obslužná rutina příslušné výjimky budou k dispozici v zásobníku.

Neexistuje pomocné funkce, nejběžnější předdefinované SCODEs, jako například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), a [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Seznam předdefinovaných SCODEs a pokyny k definování vlastní SCODEs, najdete v části [zpracování chyb v svůj ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Advanced témata.

Další informace o vytváření sestav výjimky v jiných oblastech, které váš kód, naleznete v tématu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [zpracování chyb v svůj ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Advanced témata.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

