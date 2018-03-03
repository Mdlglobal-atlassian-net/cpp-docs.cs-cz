---
title: "Třída CStringElementTraits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 025c9aa66a8647fd5d8ca9803aedb50b27ed3be1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits – třída
Tato třída poskytuje statické funkce používá ukládání třídy kolekce `CString` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání do třídy objektu kolekce elementů.|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z kolekce třídy objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|(Statické) Volání této funkce k porovnání dvou prvků řetězce rovnosti.|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statické) Volání této funkce k porovnání dvou prvků řetězce.|  
|[CStringElementTraits::CopyElements](#copyelements)|(Statické) Volání této funkce kopírování `CString` elementy, které jsou uložené v objektu třídy kolekce.|  
|[CStringElementTraits::Hash](#hash)|(Statické) Volání této funkce Vypočítat hodnotu hash pro daný řetězec elementu.|  
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statické) Volání této funkce přesunovat `CString` elementy, které jsou uložené v objektu třídy kolekce.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje statické funkce pro kopírování, přesunutí a porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat na základě řetězce. Použití [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) při porovnávání se vyžadují. Použití [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) při řetězcových objektů je třeba řešit s jako odkazy.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cstringt.h  
  
##  <a name="compareelements"></a>CStringElementTraits::CompareElements  
 Volání této statické funkce k porovnání dvou prvků řetězce rovnosti.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec elementu.  
  
 `str2`  
 Druhý řetězec elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud elementy jsou stejné, jinak hodnota false.  
  
##  <a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered  
 Volání této statické funkce k porovnání dvou prvků řetězce.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 První řetězec elementu.  
  
 `str2`  
 Druhý řetězec elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud jsou řetězce identické, < 0 Pokud `str1` je menší než `str2`, nebo > 0 Pokud `str1` je větší než `str2`. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda se používá k provádění porovnání.  

  
##  <a name="copyelements"></a>CStringElementTraits::CopyElements  
 Volání této funkce statický zkopírovat `CString` elementy, které jsou uložené v objektu třídy kolekce.  
  
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
  
##  <a name="hash"></a>CStringElementTraits::Hash  
 Volání této statické funkce Vypočítat hodnotu hash pro daný řetězec elementu.  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Element řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu hash, vypočítává pomocí obsahu řetězce.  
  
##  <a name="inargtype"></a>CStringElementTraits::INARGTYPE  
 Datový typ pro použití při přidávání do třídy objektu kolekce elementů.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraits::OUTARGTYPE  
 Datový typ pro načítání elementy z kolekce třídy objektu.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CStringElementTraits::RelocateElements  
 Volání této funkce statický přesunovat `CString` elementy, které jsou uložené v objektu třídy kolekce.  
  
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
 Tato statická funkce volá [memmove –](../../c-runtime-library/reference/memmove-wmemmove.md), což je dostatečné pro většinu datových typů. Pokud objekty přesouvání obsahují ukazatelé na své vlastní členy, Tato statická funkce potřebovat k přepsání.  
  
## <a name="see-also"></a>Viz také  
 [CElementTraitsBase – třída](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI – třída](../../atl/reference/cstringelementtraitsi-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
