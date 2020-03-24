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
ms.openlocfilehash: a53cd653258980d21e9dd297ae61c458732b7250
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210545"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl – třída

Provede stejné funkce jako `IObjectWithSite`, ale také umožňuje OLE DB vlastnosti `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída odvozená od `IRowsetCreator`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[SetSite](#setsite)|Nastaví lokalitu, která obsahuje objekt sady řádků.|

## <a name="remarks"></a>Poznámky

Tato třída dědí z [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) a Přepisuje [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Když příkaz nebo objekt Session zprostředkovatele vytvoří sadu řádků, zavolá `QueryInterface` objektu sady řádků, který hledá `IObjectWithSite` a volání `SetSite` předání rozhraní `IUnkown` objektu sady řádků jako rozhraní lokality.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a>IRowsetCreatorImpl –:: SetSite

Nastaví lokalitu, která obsahuje objekt sady řádků. Další informace najdete v tématu [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parametry

*pCreator*<br/>
pro Ukazatel na ukazatel rozhraní `IUnknown` lokality, která spravuje objekt sady řádků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Kromě toho `IRowsetCreatorImpl::SetSite` povoluje vlastnosti `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` OLE DB.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
