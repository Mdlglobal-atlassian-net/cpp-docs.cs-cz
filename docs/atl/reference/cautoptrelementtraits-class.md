---
title: Cautoptrelementtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cab1b2699c87c09761258fcde8cbb8b4c8eaa32f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764248"
---
# <a name="cautoptrelementtraits-class"></a>Cautoptrelementtraits – třída

Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce inteligentních ukazatelů.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CAutoPtrElementTraits 
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Parametry

`T`  
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody, statické funkce a funkce TypeDef pro pomoc vytvoření třídy objektů kolekce obsahující inteligentní ukazatele. Třídy [cautoptrarray –](../../atl/reference/cautoptrarray-class.md) a [cautoptrlist –](../../atl/reference/cautoptrlist-class.md) odvozovat `CAutoPtrElementTraits`. Pokud sestavování kolekce inteligentních ukazatelů, která vyžaduje vektor – nový a operátory odstranění, použijte [cautovectorptrelementtraits –](../../atl/reference/cautovectorptrelementtraits-class.md) místo.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)

[Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)

[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)

[Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE

Datový typ pro použití při přidávání prvků do objektu třídy kolekce.

```
typedef CAutoPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE

Datový typ použitý pro získání prvky z třídy objektu kolekce.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Cdefaultelementtraits – třída](../../atl/reference/cdefaultelementtraits-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
