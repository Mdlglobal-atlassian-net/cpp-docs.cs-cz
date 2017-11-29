---
title: "Třída CDefaultCompareTraits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs: C++
helpviewer_keywords: CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a5a9a68bd220112d6e8065e273c47fdb7247096
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits – třída
Tato třída poskytuje výchozí element porovnání funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CDefaultCompareTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statické) Volání této funkci můžete porovnat dva elementy rovnosti.|  
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statické) Volání této funkce pro zjištění elementu vyšší a nižší úrovně.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída obsahuje dvě statické funkce pro porovnání prvků, které jsou uložené v objektu třídy kolekce. Tato třída je využíváno [CDefaultElementTraits třída](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="compareelements"></a>CDefaultCompareTraits::CompareElements  
 Volání této funkci můžete porovnat dva elementy rovnosti.  
  
```
static bool CompareElements(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>Parametry  
 `element1`  
 První prvek.  
  
 `element2`  
 Druhý prvkem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud elementy jsou stejné, jinak hodnota false.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce je rovnosti ( `==`) operátor. Pro objekty než jednoduché datové typy pravděpodobně bude třeba tuto funkci k přepsání.  
  
##  <a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered  
 Volání této funkce pro zjištění elementu vyšší a nižší úrovně.  
  
```
static int CompareElementsOrdered(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>Parametry  
 `element1`  
 První prvek.  
  
 `element2`  
 Druhý prvkem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí celé číslo, na základě následující tabulky:  
  
|Podmínka|Návratová hodnota|  
|---------------|------------------|  
|`element1` < `element2`|<0|  
|`element1` == `element2`|0|  
|`element1` > `element2`|>0|  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce používá `==`,  **\<** , a  **>**  operátory. Pro objekty než jednoduché datové typy pravděpodobně bude třeba tuto funkci k přepsání.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)