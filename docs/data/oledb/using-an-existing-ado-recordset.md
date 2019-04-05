---
title: Použití existující sady záznamů ADO
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: eb558bb319bb5ddb61d0383846099d708f99c627
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030474"
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

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)