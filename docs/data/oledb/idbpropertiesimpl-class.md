---
title: IDBPropertiesImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3685e6a77e4293ef65b5ee98a0aa326500cfdb2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105121"
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