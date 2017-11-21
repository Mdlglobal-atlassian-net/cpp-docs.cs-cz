---
title: "Třída CStringElementTraitsI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs: C++
helpviewer_keywords: CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f2a2cbe93826ed2cad5d33d50df119d0ff5cb298
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI – třída
Tato třída poskytuje statické funkce související s řetězce, které jsou uložené v objektech třídy kolekce. Je podobná [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale provádí porovnávání.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>  
class CStringElementTraitsI : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání do třídy objektu kolekce elementů.|  
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z kolekce třídy objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](#compareelements)|Volání této statické funkce k porovnání dvou prvků řetězce rovnosti rozdíly v případě je ignorována.|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Volání této statickou funkci můžete porovnat dva elementy řetězec rozdíly v případě je ignorována.|  
|[CStringElementTraitsI::Hash](#hash)|Volání této statické funkce Vypočítat hodnotu hash pro daný řetězec elementu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje statické funkce pro porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat na základě řetězce. Použití [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) když jsou tyto objekty řetězec s zabývat se jako odkazy.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="compareelements"></a>CStringElementTraitsI::CompareElements  
 Volání této statické funkce k porovnání dvou prvků řetězce rovnosti rozdíly v případě je ignorována.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec elementu.  
  
 `str2`  
 Druhý řetězec elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud elementy jsou stejné, jinak hodnota false.  
  
### <a name="remarks"></a>Poznámky  
 Porovnávání se nerozlišují velká písmena.  
  
##  <a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered  
 Volání této statickou funkci můžete porovnat dva elementy řetězec rozdíly v případě je ignorována.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec elementu.  
  
 `str2`  
 Druhý řetězec elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud jsou řetězce identické, < 0 Pokud `str1` je menší než `str2`, nebo > 0 Pokud `str1` je větší než `str2`. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda se používá k provádění porovnání.  

  
### <a name="remarks"></a>Poznámky  
 Porovnávání se nerozlišují velká písmena.  
  
##  <a name="hash"></a>CStringElementTraitsI::Hash  
 Volání této statické funkce Vypočítat hodnotu hash pro daný řetězec elementu.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Element řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu hash, vypočítává pomocí obsahu řetězce.  
  
##  <a name="inargtype"></a>CStringElementTraitsI::INARGTYPE  
 Datový typ pro použití při přidávání do třídy objektu kolekce elementů.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE  
 Datový typ pro načítání elementy z kolekce třídy objektu.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [CElementTraitsBase – třída](../../atl/reference/celementtraitsbase-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CStringElementTraits – třída](../../atl/reference/cstringelementtraits-class.md)
