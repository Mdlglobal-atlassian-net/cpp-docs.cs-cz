---
title: PROPERTY_INFO_ENTRY_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY_EX
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY_EX macro
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 61842dc963ae442d23f802c1fd64c037f4a882e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="propertyinfoentryex"></a>PROPERTY_INFO_ENTRY_EX
Představuje určité vlastnosti v sadu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PROPERTY_INFO_ENTRY_EX(  
dwPropID  
, vt, dwFlags, value, options )  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [v] A [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) nastavit hodnotu, kterou můžete použít ve spojení s vlastností GUID k identifikaci vlastnost.  
  
 *VT*  
 [v] [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) této vlastnosti položky.  
  
 `dwFlags`  
 [v] A [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) hodnota popisující tuto položku Vlastnosti.  
  
 *Hodnota*  
 [v] Hodnota vlastnosti typu `DWORD`.  
  
 `options`  
 Buď **DBPROPOPTIONS_REQUIRED** nebo **DBPROPOPTIONS_SETIFCHEAP**. Za normálních okolností zprostředkovatele není nutné nastavovat `options` vzhledem k tomu, že je nastavena podle příjemce.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této makro můžete přímo zadat hodnotu vlastnosti typu `DWORD` a také možnosti a značky. Výchozí hodnota definovaná v ATLDB jenom nastavit vlastnost. H, použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pokud chcete nastavit vlastnost na hodnotu dle vlastního výběru, bez možnosti nastavení nebo příznaky, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)