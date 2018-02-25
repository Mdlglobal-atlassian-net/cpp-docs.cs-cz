---
title: "CUtlProps – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- CUtlProps class
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8c8aa99a4ad1642ea14b85e3e68f00a68c005bb4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cutlprops-class"></a>CUtlProps – třída
Implementuje vlastnosti pro celou řadu vlastností rozhraní OLE DB (například `IDBProperties`, `IDBProperties`, a `IRowsetInfo`).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída, která obsahuje `BEGIN_PROPSET_MAP`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|Získá vlastnost z sadu vlastností.|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|Slouží k ověření hodnotu před nastavením vlastnosti.|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|Zpracovává požadavky pro volitelné rozhraní, když příjemce volá metodu na rozhraní vytvoření objektu.|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|Volá se po nastavení vlastností pro zpracování zřetězené vlastnosti.|  
|[Setpropvalue –](../../data/oledb/cutlprops-setpropvalue.md)|Nastaví vlastnost v sadu vlastností.|  
  
## <a name="remarks"></a>Poznámky  
 Většina této třídy je podrobností implementace.  
  
 `CUtlProps` obsahuje dva členy pro nastavení vlastností interně: [getpropvalue –](../../data/oledb/cutlprops-getpropvalue.md) a [setpropvalue –](../../data/oledb/cutlprops-setpropvalue.md).  
  
 Další informace o makra použít v mapy sady vlastností v tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) a [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)