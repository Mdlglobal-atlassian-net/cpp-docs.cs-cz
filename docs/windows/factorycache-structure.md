---
title: "Factorycache – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0fc48c9a3651e8c5a6609886862c2f73c5707638
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="factorycache-structure"></a>FactoryCache – struktura
Podporuje infrastrukturu knihovna šablon C++ prostředí Windows Runtime a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obsahuje umístění objekt pro vytváření tříd a hodnotu, která identifikuje registrovaný wrt nebo objektu COM třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[FactoryCache::cookie – datový člen](../windows/factorycache-cookie-data-member.md)|Obsahuje hodnotu, která identifikuje registrované objektu třídy prostředí Windows Runtime nebo COM a je později použít ke zrušení registrace objektu.|  
|[FactoryCache::factory – datový člen](../windows/factorycache-factory-data-member.md)|Odkazuje na objekt třídy prostředí Windows Runtime nebo COM.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `FactoryCache`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)