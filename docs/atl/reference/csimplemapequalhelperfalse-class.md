---
title: "Třída CSimpleMapEqualHelperFalse | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs: C++
helpviewer_keywords: CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1dda098f54b0589a610e10713cc2f936172e26e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse – třída
Tato třída je Pomocník pro [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statické) Testy dva klíče rovnosti.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statické) Vrátí hodnotu false.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída vlastnosti je dodatek k `CSimpleMap` třídy. Poskytuje metodu pro porovnání dva elementy, které jsou součástí `CSimpleMap` objekt, konkrétně dva elementy hodnotu nebo dvě klíčové prvky.  
  
 Porovnání hodnoty vždy vrátí hodnotu false a kromě toho bude volat `ATLASSERT` s argumentem false, pokud se někdy odkazuje. V situacích, kde není dostatečně definovány test rovnosti, tato třída umožňuje mapu obsahující dvojice klíč/hodnota k správně fungovat pro většinu metod, ale nezdaří způsobem dobře definovaný pro metody, které jsou závislé na porovnání například [CSimpleMap:: FindVal](../../atl/reference/csimplemap-class.md#findval).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey  
 Testy dva klíče rovnosti.  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>Parametry  
 `k1`  
 První klíč.  
  
 `k2`  
 Druhý klíč.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud klíče jsou stejné, jinak hodnota false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).  
  
##  <a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue  
 Vrátí hodnotu false.  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vždy vrátí hodnotu false a zavolá `ATLASSERT` s argumentem false, pokud se někdy odkazuje. Účelem `CSimpleMapEqualHelperFalse::IsEqualValue` donutit metod pomocí porovnání selhání dobře definovaný způsobem při testování rovnosti nebyly definovány adekvátní.  
  
## <a name="see-also"></a>Viz také  
 [CSimpleMapEqualHelper – třída](../../atl/reference/csimplemapequalhelper-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
