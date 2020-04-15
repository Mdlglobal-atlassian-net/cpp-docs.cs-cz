---
title: Třída CRBMap
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331396"
---
# <a name="crbmap-class"></a>Třída CRBMap

Tato třída představuje strukturu mapování pomocí červeno-černé binární strom.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíčového prvku.

*V*<br/>
Typ prvku hodnoty.

*KTraity*<br/>
Kód používaný ke kopírování nebo přesunutí klíčových prvků. Další podrobnosti najdete v [části CElementTraits Class.](../../atl/reference/celementtraits-class.md)

*VTraits*<br/>
Kód používaný ke kopírování nebo přesouvání prvků hodnoty.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|Konstruktor|
|[CRBMap::~CRBMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRBMap::Vyhledávání](#lookup)|Volání této metody vyhledat klíče nebo `CRBMap` hodnoty v objektu.|
|[CRBMap::Odebrat klíč](#removekey)|Volání této metody odebrat `CRBMap` prvek z objektu, daný klíč.|
|[CRBMap::Setat](#setat)|Volání této metody vložit pár elementů do mapy.|

## <a name="remarks"></a>Poznámky

`CRBMap`poskytuje podporu pro mapování pole libovolného daného typu, správa objednané pole klíčových prvků a jejich přidružené hodnoty. Každý klíč může mít pouze jednu přidruženou hodnotu. Elementy (skládající se z klíče a hodnoty) jsou uloženy v binární stromové struktuře pomocí metody [CRBMap::SetAt.](#setat) Prvky lze odebrat pomocí [metody CRBMap::RemoveKey,](#removekey) která odstraní prvek s danou hodnotou klíče.

Procházení stromu je možné pomocí metod, jako je [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)a [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

*Parametry KTraits* a *VTraits* jsou třídy vlastností, které obsahují jakýkoli doplňkový kód potřebný ke kopírování nebo přesouvání prvků.

`CRBMap`je odvozen z [CRBTree](../../atl/reference/crbtree-class.md), který implementuje binární strom pomocí algoritmu Red-Black. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) je varianta, která umožňuje více hodnot pro každý klíč. To také je `CRBTree`odvozen od , a `CRBMap`tak sdílí mnoho funkcí s .

Alternativa k `CRBMap` `CRBMultiMap` oběma a je nabízena třídou [CAtlMap.](../../atl/reference/catlmap-class.md) Pokud je třeba uložit pouze malý počet prvků, zvažte použití [csimplemap](../../atl/reference/csimplemap-class.md) třídy místo.

Podrobnější diskusi o různých třídách kolekce a jejich funkcích a vlastnostech výkonu naleznete [v tématu TŘÍDY kolekce atl](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Crbtree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap::CRBMap

Konstruktor

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

Parametr *nBlockSize* je míra velikosti paměti přidělené při použití nového prvku. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků. Výchozí bude přidělit místo pro 10 prvků najednou.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap::~CRBMap

Destruktor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap::Vyhledávání

Volání této metody vyhledat klíče nebo `CRBMap` hodnoty v objektu.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje prvek, který má být vyhledán.

*Hodnotu*<br/>
Proměnná, která obdrží hodnotu vyhledat.

### <a name="return-value"></a>Návratová hodnota

První forma metody vrátí true, pokud je nalezen klíč, jinak false. Druhý a třetí formulář vrátí ukazatel [na CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Poznámky

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap::Odebrat klíč

Volání této metody odebrat `CRBMap` prvek z objektu, daný klíč.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč odpovídající dvojici prvků, kterou chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je klíč nalezen a odebrán, false při selhání.

### <a name="remarks"></a>Poznámky

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>CRBMap::Setat

Volání této metody vložit pár elementů do mapy.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, kterou `CRBMap` chcete přidat k objektu.

*Hodnotu*<br/>
Hodnota, kterou chcete `CRBMap` přidat k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici páru prvků klíč/hodnota `CRBMap` v objektu.

### <a name="remarks"></a>Poznámky

`SetAt`nahradí existující prvek, pokud je nalezen odpovídající klíč. Pokud klíč není nalezen, vytvoří se nový pár klíč/hodnota.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Třída CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Třída CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Třída CRBMultiMap](../../atl/reference/crbmultimap-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
