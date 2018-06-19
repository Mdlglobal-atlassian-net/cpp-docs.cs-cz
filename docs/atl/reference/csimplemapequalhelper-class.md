---
title: Třída CSimpleMapEqualHelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4bfef99d12ae724c2ca6e70375f08a8dc1fb15b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361837"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper – třída
Tato třída je Pomocník pro [CSimpleMap](../../atl/reference/csimplemap-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```  
  
#### <a name="parameters"></a>Parametry  
 `TKey`  
 Klíčovým prvkem.  
  
 `TVal`  
 Hodnota elementu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statické) Testy dva klíče rovnosti.|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statické) Porovná dvě hodnoty rovnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída vlastnosti je dodatek k `CSimpleMap` třídy. Poskytuje metody pro porovnání dvou `CSimpleMap` objektu elementy (konkrétně klíč a hodnotu komponenty) rovnosti. Ve výchozím nastavení, klíče a hodnoty jsou porovnávány pomocí `operator==()`, ale pokud mapy obsahuje komplexní datové typy, které nemají své vlastní operátor rovnosti, tato třída může být přepsáno za velmi požadovanou funkci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey  
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
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue  
 Porovná dvě hodnoty rovnosti.  
  
```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```  
  
### <a name="parameters"></a>Parametry  
 *V1*  
 První hodnota.  
  
 *v2*  
 Druhá hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud hodnoty jsou stejné, jinak hodnota false.  
  
## <a name="see-also"></a>Viz také  
 [CSimpleMapEqualHelperFalse – třída](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
