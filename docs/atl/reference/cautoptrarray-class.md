---
title: "Třída CAutoPtrArray | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs: C++
helpviewer_keywords: CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 952f6a6d9fa06c0f0c34e5769b4302c6230abb43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray – třída
Tato třída poskytuje metody, které jsou užitečné při vytváření pole chytré ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ ukazatele.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje konstruktor a je odvozena z metody [CAtlArray](../../atl/reference/catlarray-class.md) a [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) a usnadňuje vytvoření třídy objektu kolekce ukládání chytré ukazatele.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray  
 Konstruktor  
  
```
CAutoPtrArray() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje pole chytré ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [CAtlArray – třída](../../atl/reference/catlarray-class.md)   
 [CAutoPtrElementTraits – třída](../../atl/reference/cautoptrelementtraits-class.md)   
 [CAutoPtrList – třída](../../atl/reference/cautoptrlist-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
