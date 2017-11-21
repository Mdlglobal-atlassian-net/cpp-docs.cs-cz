---
title: "Třída CComAutoDeleteCriticalSection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs: C++
helpviewer_keywords: CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d073e392030db72d6371a798875daf3d7a90e247
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection – třída
Tato třída poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Poznámky  
 `CComAutoDeleteCriticalSection`je odvozena od třídy [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Ale `CComAutoDeleteCriticalSection` přepsání [termín](ccomsafedeletecriticalsection-class.md#term) metodu `private` přístup, který vynutí interní paměť čištění proběhnout, jenom když se dostala mimo rozsah nebo jsou explicitně odstranit z paměti instance této třídy.  

  
 Tato třída představuje žádné další metody přes její základní třída. V tématu [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) a [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) Další informace o kritická sekce pomocné třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
## <a name="see-also"></a>Viz také  
 [CComSafeDeleteCriticalSection – třída](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
