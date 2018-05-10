---
title: Creatormap – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a6113737d7463354ffa273ced61b190246f63a83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="creatormap-structure"></a>CreatorMap – struktura
Podporuje infrastrukturu knihovna šablon C++ prostředí Windows Runtime a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obsahuje informace o tom, jak inicializovat, zaregistrujte a zrušit registraci objekty.  
  
 Creatormap – obsahuje následující informace:  
  
-   Způsob inicializace, registrace a zrušení registrace objekty.  
  
-   Jak k porovnání dat aktivace v závislosti na objekt COM nebo prostředí Windows Runtime classic.  
  
-   Informace o název objektu pro vytváření mezipaměti a server pro rozhraní.  
  
## <a name="members"></a>Členové  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CreatorMap::activationId – datový člen](../windows/creatormap-activationid-data-member.md)|Představuje identifikovanou classic ID třídy modelu COM nebo prostředí Windows Runtime název ID objektu.|  
|[CreatorMap::factoryCache – datový člen](../windows/creatormap-factorycache-data-member.md)|Uchovává creatormap – ukazatel na objekt pro vytváření mezipaměti.|  
|[CreatorMap::factoryCreator – datový člen](../windows/creatormap-factorycreator-data-member.md)|Vytvoří objekt factory pro zadaný creatormap –.|  
|[CreatorMap::serverName – datový člen](../windows/creatormap-servername-data-member.md)|Ukládá název serveru pro creatormap –.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CreatorMap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)