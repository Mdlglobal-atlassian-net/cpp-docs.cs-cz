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
ms.openlocfilehash: 3dc5cb06b3eb7f01667e4e1ec09dd60f9befae77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390786"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl – třída

Provádí stejné funkce jako `IObjectWithSite` ale taky umožňuje vlastnosti OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

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

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[SetSite](#setsite)|Nastaví lokalitu, která obsahuje objektu sady řádků.|

## <a name="remarks"></a>Poznámky

Tato třída dědí z [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) a přepíše [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Vytvoří objekt příkazu nebo v jiné relaci zprostředkovatele sady řádků, volá `QueryInterface` na objektu sady řádků hledáte `IObjectWithSite` a volání `SetSite` předání objektu sady řádků `IUnkown` rozhraní jako rozhraní webu.

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

Nastaví lokalitu, která obsahuje objektu sady řádků. Další informace najdete v tématu [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parametry

*pCreator*<br/>
[in] Ukazatel `IUnknown` ukazatel rozhraní objektu sady řádků Správa lokality.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Kromě toho `IRowsetCreatorImpl::SetSite` umožňuje OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` vlastnosti.

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)