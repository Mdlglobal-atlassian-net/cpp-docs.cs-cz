---
title: "IDBCreateSessionImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
dev_langs: C++
helpviewer_keywords: IDBCreateSessionImpl class
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5f8cb4e35c14ddbb8a7f8df3fe3686025cf5eae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl – třída
Poskytuje implementaci pro [IDBCreateSession](https://msdn.microsoft.com/en-us/library/ms724076.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 VAŠE TŘÍDY ODVOZENÉ OD  
  
 `SessionClass`  
 Objekt relace.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Vytvoření relace](../../data/oledb/idbcreatesessionimpl-createsession.md)|Vytvoří novou relaci z objekt zdroje dat a vrátí požadované rozhraní v nově vytvořené relace.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní na objekty zdroje dat.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)