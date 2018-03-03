---
title: "Creatormap – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a941f052527b3617772bcb18b2092fdc35ea3a22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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