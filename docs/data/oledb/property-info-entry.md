---
title: PROPERTY_INFO_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROPERTY_INFO_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d660a969937e3e75784516e3b50fbfe2690f9d3c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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