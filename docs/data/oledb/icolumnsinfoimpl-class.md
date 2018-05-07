---
title: IColumnsInfoImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IColumnsInfoImpl class
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 93cc4c44031d2091de64f2d82c1866135d1702cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl – třída
Představuje implementaci objektu [IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IColumnsInfoImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetColumnInfo –](../../data/oledb/icolumnsinfoimpl-getcolumninfo.md)|Vrátí metadata sloupce potřeby většiny příjemci.|  
|[Mapcolumnids –](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)|Vrátí pole řadové číslovky sloupců v sadě řádků, které jsou určeny zadaný sloupec ID.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní na příkazy a sady řádků. Chcete-li upravit chování svého poskytovatele `IColumnsInfo` implementace, budete muset upravit mapu sloupců poskytovatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)