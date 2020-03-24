---
title: IDBCreateSessionImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: cff1ca374c9489cb9c5df0dad153c4bf7a4cbc9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210779"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl – třída

Poskytuje implementaci rozhraní [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>Parametry

*Š*<br/>
VAŠE TŘÍDA, KTERÁ JE ODVOZENA Z

*SessionClass*<br/>
Objekt Session.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[CreateSession](#createsession)|Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní v nově vytvořené relaci.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní pro objekty zdroje dat.

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a>IDBCreateSessionImpl –:: CreateSession

Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní v nově vytvořené relaci.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Parametry

Viz [IDBCreateSession:: CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
