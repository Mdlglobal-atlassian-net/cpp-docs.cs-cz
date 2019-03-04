---
title: Cautovectorptrelementtraits – třída
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 168670709470d7b7fdd77edb3c29d5a9f4049ca3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280729"
---
# <a name="cautovectorptrelementtraits-class"></a>Cautovectorptrelementtraits – třída

Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce inteligentních ukazatelů pomocí nové vektoru a odstranit operátory.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody, statické funkce a funkce TypeDef pro pomoc vytvoření třídy objektů kolekce obsahující inteligentní ukazatele. Na rozdíl od [cautoptrelementtraits –](../../atl/reference/cautoptrelementtraits-class.md), tato třída používá nové vektorové a odstraňte operátory.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)

[Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)

[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)

[Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE

Datový typ pro použití při přidávání prvků do objektu třídy kolekce.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE

Datový typ použitý pro získání prvky z třídy objektu kolekce.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také:

[CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr – třída](../../atl/reference/cautovectorptr-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
