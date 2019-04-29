---
title: IGetDataSourceImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 2056b93fd6c1d32b72996970352e87670ff406de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408937"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl – třída

Poskytuje implementaci [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IGetDataSourceImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetDataSource](#getdatasource)|Vrátí ukazatel rozhraní objektu zdroje dat, která byla relace vytvořena.|

## <a name="remarks"></a>Poznámky

Toto je povinné rozhraní relace k získání ukazatele rozhraní objektu zdroje dat.

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource

Vrátí ukazatel rozhraní objektu zdroje dat, která byla relace vytvořena.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IGetDataSource::GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Je užitečné, pokud potřebujete přístup k vlastnostem v objektu zdroje dat.

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)