---
title: Třída CDefaultElementTraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16574857f4f5bd4566fcef551fa5e56290b7ce6b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360959"
---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits – třída
Tato třída poskytuje výchozí metody a funkce pro třídu kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v kolekci.  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje výchozí statické funkce a metody pro přesun, kopírování, porovnání a hash elementy, které jsou uložené v objektu třídy kolekce. Tato třída odvozena její funkce a metody z [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), a [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)a je využíváno [ CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), a [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
