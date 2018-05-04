---
title: Třída CStringRefElementTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8746bf216be417fb569aae58421b272c983914b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits – třída
Tato třída poskytuje statické funkce související s řetězce, které jsou uložené v objektech třídy kolekce. Řetězec objekty jsou uvedeny jako odkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|Volání této statické funkce k porovnání dvou prvků řetězce rovnosti.|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Volání této statické funkce k porovnání dvou prvků řetězce.|  
|[CStringRefElementTraits::Hash](#hash)|Volání této statické funkce Vypočítat hodnotu hash pro daný řetězec elementu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje statické funkce pro porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat na základě řetězce. Na rozdíl od [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) a [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` způsobí, že `CString` argumenty, které mají být předány jako **const CString &** odkazy.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements  
 Volání této statické funkce k porovnání dvou prvků řetězce rovnosti.  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `element1`  
 První řetězec elementu.  
  
 `element2`  
 Druhý řetězec elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud elementy jsou stejné, jinak hodnota false.  
  
##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered  
 Volání této statické funkce k porovnání dvou prvků řetězce.  
  
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
  
##  <a name="hash"></a>  CStringRefElementTraits::Hash  
 Volání této statické funkce Vypočítat hodnotu hash pro daný řetězec elementu.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Element řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu hash, vypočítává pomocí obsahu řetězce.  
  
## <a name="see-also"></a>Viz také  
 [CElementTraitsBase – třída](../../atl/reference/celementtraitsbase-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
