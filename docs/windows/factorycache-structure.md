---
title: "Factorycache – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::FactoryCache
dev_langs: C++
helpviewer_keywords: FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb6b32fbd34794c13d2f4b7dc75e242464bc7b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Factorycache::cookie – datový člen](../windows/factorycache-cookie-data-member.md)|Obsahuje hodnotu, která identifikuje registrované objektu třídy prostředí Windows Runtime nebo COM a je později použít ke zrušení registrace objektu.|  
|[Factorycache::Factory – datový člen](../windows/factorycache-factory-data-member.md)|Odkazuje na objekt třídy prostředí Windows Runtime nebo COM.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `FactoryCache`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)