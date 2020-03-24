---
title: IDBCreateCommandImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 4a4978401ba90e3a7a91ac40cc1b0668adf12ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210714"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl – třída

Poskytuje implementaci rozhraní [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Objekt Session odvozený z `IDBCreateCommandImpl`.

*CommandClass*<br/>
Vaše třída příkazu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[CreateCommand](#createcommand)|Vytvoří nový příkaz.|

## <a name="remarks"></a>Poznámky

Volitelné rozhraní objektu Session pro získání nového příkazu.

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a>IDBCreateCommandImpl –:: CreateCommand

Vytvoří nový příkaz a vrátí požadované rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parametry

Viz [IDBCreateCommand:: CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) v *referenci programátora OLE DB*.

Některé parametry odpovídají *OLE DB referenční parametry programátora* různých názvů, které jsou popsány v `IDBCreateCommand::CreateCommand`:

|Parametry šablony OLE DB|*OLE DB referenční parametry programátora*|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
