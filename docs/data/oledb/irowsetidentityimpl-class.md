---
title: IRowsetIdentityImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 5ce4db130f4e8569b666047ca7a5c2bc4e0e6cb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593190"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl – třída

Implementuje rozhraní OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913) rozhraní, které umožňují testování pro řádek identitu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída odvozená z `IRowsetIdentityImpl`.

*RowClass*<br/>
Jednotka pro ukládání `HROW`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Issamerow –](#issamerow)|Porovná dvě popisovačů řádků zjistěte odkazují na stejný řádek.|

## <a name="issamerow"></a> IRowsetIdentityImpl::IsSameRow

Porovná dvě popisovačů řádků zjistěte odkazují na stejný řádek.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Pokud chcete porovnat popisovačů řádků, tato metoda přetypování `HROW` popisovače `RowClass` členy a volání `memcmp` na ukazatelů.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)