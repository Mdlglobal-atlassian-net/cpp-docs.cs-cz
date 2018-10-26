---
title: Idbcreatesessionimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 40856f33de8bd12ce6bc4e3f4c6ff0ced9c67be4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053722"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl – třída

Poskytuje implementaci pro [IDBCreateSession](/previous-versions/windows/desktop/ms724076) rozhraní.

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
|[Vytvoření relace](#createsession)|Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní na nově vytvořené relace.|

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

Zobrazit [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942) v *referenční informace pro OLE DB programátory*.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)