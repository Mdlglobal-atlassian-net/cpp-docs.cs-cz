---
title: Factorycache::cookie – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache::cookie
dev_langs:
- C++
helpviewer_keywords:
- cookie data member
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3636cdb2c30d08547fd9085141aa9283bdc85c7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652378"
---
# <a name="factorycachecookie-data-member"></a>FactoryCache::cookie – datový člen
Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
union {   
   WINRT_REGISTRATION_COOKIE winrt;  
   DWORD com;   
} cookie;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obsahuje hodnotu, která identifikuje registrovaného objektu třídy Windows Runtime nebo modelu COM a je později použít ke zrušení registrace objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Factorycache – struktura](../windows/factorycache-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)