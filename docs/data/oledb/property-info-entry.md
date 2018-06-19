---
title: PROPERTY_INFO_ENTRY | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2603d3257edad6e90357c425a8b5aef60af611dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105189"
---
# <a name="propertyinfoentry"></a>PROPERTY_INFO_ENTRY
Představuje určité vlastnosti v sadu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [v] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) nastavit hodnotu, kterou můžete použít ve spojení s vlastností GUID k identifikaci vlastnost.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro nastaví hodnotu vlastnosti typu `DWORD` na výchozí hodnotu definované v ATLDB. H. Chcete-li vlastnost nastavena na hodnotu dle vlastního výběru, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Chcete-li nastavit [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) a [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) pro vlastnost ve stejnou dobu, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)