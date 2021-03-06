---
title: IRowsetIdentityImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 20f558099c02d7de8a20b3cf631812b44a742a48
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210402"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl – třída

Implementuje rozhraní OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85)) , které umožňuje testování pro identitu řádku.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída odvozená od `IRowsetIdentityImpl`.

*RowClass*<br/>
Jednotka úložiště pro `HROW`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[IsSameRow](#issamerow)|Porovná dva popisovače řádků a zjistí, zda odkazují na stejný řádek.|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a>IRowsetIdentityImpl –:: IsSameRow

Porovná dva popisovače řádků a zjistí, zda odkazují na stejný řádek.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Pro porovnání popisovačů řádků Tato metoda přetypování `HROW` popisovačů `RowClass` členů a volání `memcmp` na ukazateli.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
