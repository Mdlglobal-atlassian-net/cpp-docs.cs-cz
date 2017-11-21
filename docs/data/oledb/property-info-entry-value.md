---
title: PROPERTY_INFO_ENTRY_VALUE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY_VALUE
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY_VALUE macro
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25eb1627f4024fd18dbf0d22114c2e762ab8b897
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="propertyinfoentryvalue"></a>PROPERTY_INFO_ENTRY_VALUE
Představuje určité vlastnosti v sadu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PROPERTY_INFO_ENTRY_VALUE(  
dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [v] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) nastavit hodnotu, kterou můžete použít ve spojení s vlastností GUID k identifikaci vlastnost.  
  
 *Hodnota*  
 [v] Hodnota vlastnosti typu `DWORD`.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této makro můžete přímo zadat hodnotu vlastnosti typu `DWORD`. Chcete-li vlastnost na výchozí hodnotu definovanou v ATLDB. H, použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pokud chcete nastavit hodnoty, příznaky a možnosti pro vlastnost, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)