---
title: Cautoptrlist – třída
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: a7e5c2db31100da8901deaae61527c65655faa7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551408"
---
# <a name="cautoptrlist-class"></a>Cautoptrlist – třída

Tato třída poskytuje metody, které jsou užitečné při vytváření seznamu inteligentní ukazatele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a je odvozena z metody [catllist –](../../atl/reference/catllist-class.md) a [cautoptrelementtraits –](../../atl/reference/cautoptrelementtraits-class.md) pro podporu vytvoření seznamu objektů ukládání inteligentní ukazatele. Třída [cautoptrarray –](../../atl/reference/cautoptrarray-class.md) poskytuje podobné funkce pro objekt typu pole.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Catllist –](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList

Konstruktor

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku, výchozí hodnota je 10.

### <a name="remarks"></a>Poznámky

Velikost bloku je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.

## <a name="see-also"></a>Viz také

[CAtlList – třída](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits – třída](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
