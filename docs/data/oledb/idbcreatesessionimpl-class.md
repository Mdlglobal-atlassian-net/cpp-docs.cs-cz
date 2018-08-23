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
ms.openlocfilehash: d934e9ae5494b934acb0779665ba4471dfc4c2b7
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464714"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl – třída
Poskytuje implementaci pro [IDBCreateSession](/previous-versions/windows/desktop/ms724076\(v=vs.85\)) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 VAŠI TŘÍDU ODVOZENOU Z  
  
 *SessionClass*  
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
 Zobrazit [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.   
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)