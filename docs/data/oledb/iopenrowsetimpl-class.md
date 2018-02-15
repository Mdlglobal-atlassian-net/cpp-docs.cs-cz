---
title: "IOpenRowsetImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOpenRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa59f1a4f8b599cc74cbe824815c65b60e7b6af1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl – třída
Poskytuje implementaci pro `IOpenRowset` rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `SessionClass`  
 Vlastní třídy odvozené od `IOpenRowsetImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|Vytvoří objekt sady řádků. Není volána přímo uživatelem.|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|Otevře a vrací sadu řádků, který zahrnuje všechny řádky z jedné základní tabulky nebo indexu. (Ne ve ATLDB. H)|  
  
## <a name="remarks"></a>Poznámky  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) rozhraní je povinné pro objekt relace. Otevře a vrací sadu řádků, který zahrnuje všechny řádky z jedné základní tabulky nebo indexu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)