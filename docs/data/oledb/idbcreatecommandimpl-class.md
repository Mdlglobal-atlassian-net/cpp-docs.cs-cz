---
title: IDBCreateCommandImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 7450d91cd5e5383b55e2ebb391fe5f1190cbed2a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024926"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl – třída

Poskytuje implementaci [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Parametry

*T*<br/>
Relace objekt odvozený od `IDBCreateCommandImpl`.

*CommandClass*<br/>
Vaší třídy příkazu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[CreateCommand](#createcommand)|Vytvoří nový příkaz.|

## <a name="remarks"></a>Poznámky

Volitelné rozhraní objektu relace získat nový příkaz.

## <a name="createcommand"></a> IDBCreateCommandImpl::CreateCommand

Vytvoří nový příkaz a vrátí požadované rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) v *referenční informace pro OLE DB programátory*.

Některé parametry odpovídají *OLE DB referenční informace pro programátory* parametry jiné názvy, které jsou popsány v `IDBCreateCommand::CreateCommand`:

|Parametry šablony technologie OLE DB|*OLE DB referenční informace pro programátory* parametry|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)