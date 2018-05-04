---
title: Třída CSimpleArrayEqualHelperFalse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e22d67634f29b60bdc983c892c5fe266df61d08
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse – třída
Tato třída je Pomocník pro [CSimpleArray](../../atl/reference/csimplearray-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Odvozené třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statické) Vrátí hodnotu false.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída vlastnosti je doplněk `CSimpleArray` třídy. IT vždy vrátí hodnotu false a kromě toho bude volat `ATLASSERT` s argumentem false, pokud se někdy odkazuje. V situacích, kde není dostatečně definovány test rovnosti, tato třída umožňuje pole obsahující elementy správně fungovat pro většinu metod ale selhání způsobem dobře definovaný pro metody, které jsou závislé na porovnání například [CSimpleArray:: Najít](../../atl/reference/csimplearray-class.md#find).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpcoll.h  
  
##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual  
 Vrátí hodnotu false.  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vždy vrátí hodnotu false a zavolá `ATLASSERT` s argumentem false, pokud odkazuje. Účelem `CSimpleArrayEqualHelperFalse::IsEqual` donutit metod pomocí porovnání selhání dobře definovaný způsobem při testování rovnosti nebyly definovány adekvátní.  
  
## <a name="see-also"></a>Viz také  
 [CSimpleArrayEqualHelper – třída](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
