---
title: Použití existující sady záznamů ADO
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209349"
---
# <a name="using-an-existing-ado-recordset"></a>Použití existující sady záznamů ADO

Ke smíchání OLE DBch zákaznických šablon a objektů ADO (Active Data Objects) použijte objekty ADO k otevření sady záznamů (odpovídající sadě řádků v šablonách spotřebitelů OLE DB). Pokud máte sadu záznamů, připojte se k OLE DB sadě řádků následujícím způsobem:

1. Zavolejte `QueryInterface` pro ukazatele `IRowset` a `IAccessor`.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* odkazuje na objekt `IUnknown` sady záznamů ADO.

1. Připojte přistupující objekt a sadu řádků ke svým příslušným OLE DB tříd šablon příjemce.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
