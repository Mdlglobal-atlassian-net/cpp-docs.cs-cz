---
title: "Třída CElementTraitsBase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs: C++
helpviewer_keywords: CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d0201ecd971b13b69e210b356ba9192bfdc89a54
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase – třída
Tato třída poskytuje výchozí kopírovat a přesouvat metody pro třídu kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání do třídy objektu kolekce elementů.|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z kolekce třídy objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|Voláním této metody lze kopírovat prvky, které jsou uložené v objektu třídy kolekce.|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|Volejte tuto metodu přesunovat elementy, které jsou uložené v objektu třídy kolekce.|  
  
## <a name="remarks"></a>Poznámky  
 Tato základní třída definuje metody pro kopírování a přemístění elementů ve třídě kolekce. Je využíváno třídy [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), a [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 Voláním této metody lze kopírovat prvky, které jsou uložené v objektu třídy kolekce.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parametry  
 `pDest`  
 Ukazatel na první prvek, který obdrží zkopírovaná data.  
  
 `pSrc`  
 Ukazatel na první prvek pro kopírování.  
  
 `nElements`  
 Počet elementů pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojové a cílové elementy se nesmí překrývat.  
  
##  <a name="inargtype"></a>CElementTraitsBase::INARGTYPE  
 Datový typ pro použití při přidávání prvků do kolekce.  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE  
 Datový typ pro načítání elementy z kolekce.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 Volejte tuto metodu přesunovat elementy, které jsou uložené v objektu třídy kolekce.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parametry  
 `pDest`  
 Ukazatel na první prvek, který bude přijímat přemístěné data.  
  
 `pSrc`  
 Ukazatel na první prvek přesunovat.  
  
 `nElements`  
 Počet elementů přesunovat.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [memmove –](../../c-runtime-library/reference/memmove-wmemmove.md), což je dostatečné pro většinu datových typů. Pokud objekty přesouvání obsahují ukazatelé na své vlastní členy, tato metoda potřebovat k přepsání.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
