---
title: Csimplearrayequalhelperfalse – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: a325da2edd4af8b8b0e6e965dc60df8c11bf8d30
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882855"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Csimplearrayequalhelperfalse – třída
Tato třída je pomocné rutiny pro [csimplearray –](../../atl/reference/csimplearray-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Odvozené třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statické) Vrátí hodnotu false.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída vlastností je doplněk k `CSimpleArray` třídy. IT vždy vrátí hodnotu false a kromě toho bude volat `ATLASSERT` s argumentem false, pokud se na ni stále odkazuje. V situacích, kde není dostatečně definovány test rovnosti, tato třída umožňuje pole obsahující prvky, aby správně fungovat pro většinu metod ale selhání způsobem jasně definovaných pro metody, které jsou závislé na porovnání například [csimplearray –:: Najít](../../atl/reference/csimplearray-class.md#find).  
  
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
 Tato metoda vždy vrátí hodnotu false a bude volat `ATLASSERT` s argumentem false, pokud odkazuje. Účelem `CSimpleArrayEqualHelperFalse::IsEqual` metodou je vynutit metod pomocí porovnávání selhání způsobem jasně definované při rovnosti testy nebyly definovány odpovídajícím způsobem.  
  
## <a name="see-also"></a>Viz také  
 [Csimplearrayequalhelper – třída](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
