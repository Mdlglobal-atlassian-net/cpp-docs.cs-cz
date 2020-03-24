---
title: CAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212300"
---
# <a name="caccessor-class"></a>CAccessor – třída

Představuje jeden z typů přistupujícího objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída záznamu uživatele.

## <a name="remarks"></a>Poznámky

Používá se, když je záznam staticky svázán se zdrojem dat. Záznam obsahuje vyrovnávací paměť. Tato třída podporuje více přístupových objektů pro sadu řádků.

Tento typ přístupového objektu použijte, když znáte strukturu a typ databáze.

Pokud váš přistupující objekt obsahuje pole, která odkazují na paměť (například `BSTR` nebo rozhraní), která musí být uvolněna, zavolejte členskou funkci [CAccessorRowset –:: FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) před čtením dalšího záznamu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
