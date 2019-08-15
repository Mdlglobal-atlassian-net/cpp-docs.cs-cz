---
title: IRowsetCreatorImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 8c4253d469c510f5e6eb996ed510ef836844899d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501392"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl – třída

Provádí stejné funkce jako `IObjectWithSite` , ale také umožňuje OLE DB vlastnosti. `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída odvozená z `IRowsetCreator`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[SetSite](#setsite)|Nastaví lokalitu, která obsahuje objekt sady řádků.|

## <a name="remarks"></a>Poznámky

Tato třída dědí z [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) a Přepisuje [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Když příkaz nebo objekt relace vytvoří sadu řádků, zavolá `QueryInterface` na objekt sady řádků, který `IObjectWithSite` hledá a volá `SetSite` předání `IUnkown` rozhraní objektu sady řádků jako rozhraní lokality.

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

Nastaví lokalitu, která obsahuje objekt sady řádků. Další informace najdete v tématu [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parametry

*pCreator*<br/>
pro Ukazatel na `IUnknown` ukazatel rozhraní lokality, která spravuje objekt sady řádků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Kromě toho `IRowsetCreatorImpl::SetSite` umožňuje OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` vlastnosti.

## <a name="see-also"></a>Viz také:

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)