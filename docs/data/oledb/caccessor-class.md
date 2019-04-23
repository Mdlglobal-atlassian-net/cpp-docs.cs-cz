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
ms.openlocfilehash: cfc91f971fc975bcdd2c8ae37d798ff2f5a1cab0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039199"
---
# <a name="caccessor-class"></a>CAccessor – třída

Představuje jeden z typů přistupujícího objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída uživatelského záznamu.

## <a name="remarks"></a>Poznámky

Používá se při záznamu je staticky svázán se zdrojem dat. Záznam obsahuje vyrovnávací paměti. Tato třída podporuje několik přístupových objektů pro sadu řádků.

Pomocí tohoto typu přístupového objektu, když víte, struktury a typ databáze.

Pokud váš přístupový objekt obsahuje pole, které odkazují na paměť (například `BSTR` nebo rozhraní), který musí být uvolněn zavolat členskou funkci [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) před další záznam pro čtení.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)