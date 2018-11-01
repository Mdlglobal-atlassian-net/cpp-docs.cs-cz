---
title: COM – vstupní body rozhraní
ms.date: 11/04/2016
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: b608b200094cc522d5b70e154d342108fd00892f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484770"
---
# <a name="com-interface-entry-points"></a>COM – vstupní body rozhraní

Členské funkce rozhraní modelu COM, použijte [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) – makro zajistit správné globální stav při volání metody z exportovaného rozhraní.

Obvykle, členské funkce rozhraní implementované `CCmdTarget`-odvozené objekty zajistit Automatická inicializace již použít toto makro `pThis` ukazatele. Příklad:

[!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]

Další informace najdete v tématu [technická Poznámka: 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) v MFC/OLE `IUnknown` implementace.

`METHOD_PROLOGUE` Makro je definováno jako:

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \

```

Část týkají správy globální stav – makro je:

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

V tomto výrazu *m_pModuleState* je považován za členské proměnné nadřazeného objektu. Je implementováno `CCmdTarget` základní třídy a je inicializován na odpovídající hodnotu `COleObjectFactory`, když je vytvořena instance objektu.

## <a name="see-also"></a>Viz také

[Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

