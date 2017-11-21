---
title: "Creatormap – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs: C++
helpviewer_keywords: CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c61238a809da49686975acbfb8016996cf5d5c1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Creatormap::activationid – datový člen](../windows/creatormap-activationid-data-member.md)|Představuje identifikovanou classic ID třídy modelu COM nebo prostředí Windows Runtime název ID objektu.|  
|[Creatormap::factorycache – datový člen](../windows/creatormap-factorycache-data-member.md)|Uchovává creatormap – ukazatel na objekt pro vytváření mezipaměti.|  
|[Creatormap::factorycreator – datový člen](../windows/creatormap-factorycreator-data-member.md)|Vytvoří objekt factory pro zadaný creatormap –.|  
|[Creatormap::servername – datový člen](../windows/creatormap-servername-data-member.md)|Ukládá název serveru pro creatormap –.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CreatorMap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)