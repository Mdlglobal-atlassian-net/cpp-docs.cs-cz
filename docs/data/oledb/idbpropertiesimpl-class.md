---
title: "IDBPropertiesImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2cc488ac71afedaaf590ef93dbc8d43997e30d0c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl – třída
Poskytuje implementaci pro `IDBProperties` rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IDBPropertiesImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties –](../../data/oledb/idbpropertiesimpl-getproperties.md)|Vrátí hodnoty vlastností v zdroj dat, informace o zdroji dat a inicializační vlastnosti skupiny, které jsou aktuálně nastavené na objekt zdroje dat nebo hodnoty vlastností ve skupině inicializace vlastnost, která jsou aktuálně nastavena na Enumerátor.|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|Vrací informace o všech vlastnostech podporovaných zprostředkovatelem.|  
|[SetProperties –](../../data/oledb/idbpropertiesimpl-setproperties.md)|Nastaví vlastnosti ve zdroji dat a inicializační vlastnosti skupiny, pro objekty zdroje dat, nebo skupině vlastností inicializace pro výčty.|  
  
## <a name="remarks"></a>Poznámky  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx) je povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro výčty. Ale pokud enumerátor zpřístupní [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx), musí vystavit `IDBProperties`. `IDBPropertiesImpl` implementuje `IDBProperties` pomocí statické funkce definované [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)