---
title: Cheapptrelementtraits – třída
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: 4e5d66c3e596383fecfcf730c81c4d41c08d5e2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610134"
---
# <a name="cheapptrelementtraits-class"></a>Cheapptrelementtraits – třída

Tato třída poskytuje metody, statické funkce a definice TypeDef, které jsou užitečné při vytváření kolekce haldy ukazatelů.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu ukládaly ve třídě kolekce.

*Allocator –*<br/>
Třída přidělení paměti pro použití. Výchozí hodnota je [ccrtallocator –](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody, statické funkce a funkce TypeDef pro pomoc zřízení objekty třídy kolekcí obsahujících ukazatele haldy. Třída `CHeapPtrList` je odvozena z `CHeapPtrElementTraits`.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)

[Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)

[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)

[Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE

Datový typ pro použití při přidávání prvků do objektu třídy kolekce.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE

Datový typ použitý pro získání prvky z třídy objektu kolekce.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr – třída](../../atl/reference/ccomheapptr-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
