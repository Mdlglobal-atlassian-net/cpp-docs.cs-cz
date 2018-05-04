---
title: Třída CSimpleArrayEqualHelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6660f72dbd91a41670b3c5f8772d21caf4b8abc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper – třída
Tato třída je Pomocník pro [CSimpleArray](../../atl/reference/csimplearray-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Odvozené třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statické) Dva testy `CSimpleArray` objektu elementy rovnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída vlastnosti je dodatek k `CSimpleArray` třídy. Poskytuje metodu pro porovnání dva elementy uložené v `CSimpleArray` objektu. Ve výchozím nastavení, jsou porovnávány elementy pomocí **operator=()**, ale pokud pole obsahuje komplexní datové typy, které nemají své vlastní operátor rovnosti, je nutné přepsat tuto třídu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpcoll.h  
  
##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual  
 Dva testy `CSimpleArray` objektu elementy rovnosti.  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>Parametry  
 *T1*  
 Objekt typu T.  
  
 *T2*  
 Objekt typu T.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud elementy jsou stejné, jinak hodnota false.  
  
## <a name="see-also"></a>Viz také  
 [CSimpleArray – třída](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse – třída](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
