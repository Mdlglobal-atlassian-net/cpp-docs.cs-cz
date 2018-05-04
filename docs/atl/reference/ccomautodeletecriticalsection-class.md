---
title: Třída CComAutoDeleteCriticalSection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5153520b5a5648f8352465031264c223ffd97c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection – třída
Tato třída poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>Poznámky  
 `CComAutoDeleteCriticalSection` je odvozena od třídy [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Ale `CComAutoDeleteCriticalSection` přepsání [termín](ccomsafedeletecriticalsection-class.md#term) metodu `private` přístup, který vynutí interní paměť čištění proběhnout, jenom když se dostala mimo rozsah nebo jsou explicitně odstranit z paměti instance této třídy.  

  
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
