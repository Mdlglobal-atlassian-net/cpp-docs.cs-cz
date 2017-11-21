---
title: "Třída CSimpleArrayEqualHelper | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs: C++
helpviewer_keywords: CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d53e09c64aa19b4e843297b64bad132c64a75a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
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
