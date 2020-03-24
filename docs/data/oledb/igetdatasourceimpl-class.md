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
ms.openlocfilehash: 596dd2ea7f65040ae526662974d210c1f99a0cf2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210610"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl – třída

Poskytuje implementaci objektu [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IGetDataSourceImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetDataSource](#getdatasource)|Vrátí ukazatel rozhraní u objektu zdroje dat, který vytvořil relaci.|

## <a name="remarks"></a>Poznámky

Toto je povinné rozhraní v relaci pro získání ukazatele rozhraní na objekt zdroje dat.

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a>IGetDataSourceImpl –:: GetDataSource

Vrátí ukazatel rozhraní u objektu zdroje dat, který vytvořil relaci.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parametry

Viz [IGetDataSource:: GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Užitečné v případě, že potřebujete získat přístup k vlastnostem v objektu zdroje dat.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
