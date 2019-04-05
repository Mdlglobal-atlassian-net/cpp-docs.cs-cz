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
ms.openlocfilehash: ae59abc542a4599d289c099801fc34d56b2b13d4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028532"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl – třída

Poskytuje implementaci pro [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>Parametry

*T*<br/>
VAŠI TŘÍDU ODVOZENOU Z

*SessionClass*<br/>
Objekt relace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[CreateSession](#createsession)|Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní na nově vytvořené relace.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní na objekty zdroje dat

## <a name="createsession"></a> IDBCreateSessionImpl::CreateSession

Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní na nově vytvořené relace.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)