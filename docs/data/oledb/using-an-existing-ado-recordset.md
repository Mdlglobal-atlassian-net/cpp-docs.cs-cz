---
title: Použití existující sady záznamů ADO
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 62e56b818a766bf3b7efddf9243ffd47ad2cb46f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610597"
---
# <a name="using-an-existing-ado-recordset"></a>Použití existující sady záznamů ADO

Pokud chcete kombinovat technologie OLE DB – šablony příjemce a objekty aktivní Data (ADO), použijte ADO otevřít sadu záznamů (odpovídající sady řádků v šablony příjemce technologie OLE DB). Až budete mít na sadu záznamů, proveďte postup pro připojení sady řádků OLE DB:

1. Volání `QueryInterface` pro `IRowset` a `IAccessor` ukazatele.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* odkazuje `IUnknown` objekt sady záznamů ADO.

1. Připojení k jejich příslušné třídy šablony příjemce technologie OLE DB přistupující objekt a řádků.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)