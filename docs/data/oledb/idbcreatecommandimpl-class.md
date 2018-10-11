---
title: Idbcreatecommandimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b06d6c730562203cdef1191a9d73012c3b19c2c8
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083959"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl – třída

Poskytuje implementaci [IDBCreateCommand](/previous-versions/windows/desktop/ms711625) rozhraní.  
  
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

Zobrazit [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772) v *referenční informace pro OLE DB programátory*.  
  
Některé parametry odpovídají *OLE DB referenční informace pro programátory* parametry jiné názvy, které jsou popsány v `IDBCreateCommand::CreateCommand`:  
  
|Parametry šablony technologie OLE DB|*OLE DB referenční informace pro programátory* parametry|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)