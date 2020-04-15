---
title: Třída CRBMultiMap
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331425"
---
# <a name="crbmultimap-class"></a>Třída CRBMultiMap

Tato třída představuje strukturu mapování, která umožňuje každý klíč může být přidružen a více než jednu hodnotu, pomocí červeno-černý binární strom.

## <a name="syntax"></a>Syntaxe

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Konstruktor|
|[CRBMultiMap::~CRBMultiMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Volání této metody najít pozici prvního prvku s daným klíčem.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Volání této metody získat hodnotu přidruženou k danému klíči a aktualizovat hodnotu pozice.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Volání této metody získat prvek přidružený k danému klíči a aktualizovat hodnotu pozice.|
|[CRBMultiMap::Vložit](#insert)|Volání této metody vložit pár elementů do mapy.|
|[CRBMultiMap::Odebrat klíč](#removekey)|Volání této metody odebrat všechny prvky klíč/hodnota pro daný klíč.|

## <a name="remarks"></a>Poznámky

`CRBMultiMap`poskytuje podporu pro mapování pole libovolného typu, správa objednané pole klíčových prvků a hodnot. Na rozdíl od [crbmap](../../atl/reference/crbmap-class.md) třídy každý klíč může být přidružen a více než jednu hodnotu.

Prvky (skládající se z klíče a hodnoty) jsou uloženy v binární stromové struktuře pomocí metody [CRBMultiMap::Insert.](#insert) Prvky lze odebrat pomocí [metody CRBMultiMap::RemoveKey,](#removekey) která odstraní všechny prvky, které odpovídají danému klíči.

Procházení stromu je možné pomocí metod, jako je [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)a [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Přístup k potenciálně více hodnotám na klíč je možný pomocí metod [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)a [CRBMultiMap::GetNextWithKey.](#getnextwithkey) Viz příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap) pro ilustraci tohoto v praxi.

*Parametry KTraits* a *VTraits* jsou třídy vlastností, které obsahují jakýkoli doplňkový kód potřebný ke kopírování nebo přesouvání prvků.

`CRBMultiMap`je odvozen z [CRBTree](../../atl/reference/crbtree-class.md), který implementuje binární strom pomocí algoritmu Red-Black. Alternativa `CRBMultiMap` a `CRBMap` je nabízena třídou [CAtlMap.](../../atl/reference/catlmap-class.md) Pokud je třeba uložit pouze malý počet prvků, zvažte použití [csimplemap](../../atl/reference/csimplemap-class.md) třídy místo.

Podrobnější diskusi o různých třídách kolekce a jejich funkcích a vlastnostech výkonu naleznete [v tématu TŘÍDY kolekce atl](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Crbtree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap

Konstruktor

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

Parametr *nBlockSize* je míra velikosti paměti přidělené při použití nového prvku. Větší velikosti bloků snižují volání rutiny přidělení paměti, ale používají více prostředků. Výchozí bude přidělit místo pro 10 prvků najednou.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRBMultiMap::~CRBMultiMap

Destruktor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRBMultiMap::FindFirstWithKey

Volání této metody najít pozici prvního prvku s daným klíčem.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje prvek, který má být nalezen.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici prvního prvku klíč/hodnota, pokud je nalezen klíč, NULL jinak.

### <a name="remarks"></a>Poznámky

Klíč v `CRBMultiMap` může mít jednu nebo více přidružených hodnot. Tato metoda poskytne hodnotu pozice první hodnoty (což může být ve skutečnosti jedinou hodnotou) přidruženou k tomuto konkrétnímu klíči. Vrácená hodnota pozice pak může být použita s [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) nebo [CRBMultiMap::GetNextWithKey](#getnextwithkey) k získání hodnoty a aktualizaci pozice.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

Viz příklad [crbmultimap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey

Volání této metody získat hodnotu přidruženou k danému klíči a aktualizovat hodnotu pozice.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota pozice získaná buď voláním [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) nebo [CRBMultiMap::GetNextWithKey](#getnextwithkey)nebo předchozí volání `GetNextValueWithKey`.

*key*<br/>
Určuje klíč, který identifikuje prvek, který má být nalezen.

### <a name="return-value"></a>Návratová hodnota

Vrátí dvojici prvků přidruženou k danému klíči.

### <a name="remarks"></a>Poznámky

Hodnota pozice je aktualizována tak, aby ukazovala na další hodnotu přidruženou ke klíči. Pokud neexistují žádné další hodnoty, hodnota pozice je nastavena na hodnotu NULL.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

Viz příklad [crbmultimap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey

Volání této metody získat prvek přidružený k danému klíči a aktualizovat hodnotu pozice.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota pozice získaná buď voláním [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) nebo [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)nebo předchozí volání `GetNextWithKey`.

*key*<br/>
Určuje klíč, který identifikuje prvek, který má být nalezen.

### <a name="return-value"></a>Návratová hodnota

Vrátí další [crbtree::CPair Class](crbtree-class.md#cpair_class) element přidružený k danému klíči.

### <a name="remarks"></a>Poznámky

Hodnota pozice je aktualizována tak, aby ukazovala na další hodnotu přidruženou ke klíči. Pokud neexistují žádné další hodnoty, hodnota pozice je nastavena na hodnotu NULL.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRBMultiMap::Vložit

Volání této metody vložit pár elementů do mapy.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, kterou `CRBMultiMap` chcete přidat k objektu.

*Hodnotu*<br/>
Hodnota, kterou chcete `CRBMultiMap` přidat k objektu, přidružená ke *klíči*.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici páru prvků klíč/hodnota `CRBMultiMap` v objektu.

### <a name="remarks"></a>Poznámky

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

Viz příklad [crbmultimap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRBMultiMap::Odebrat klíč

Volání této metody odebrat všechny prvky klíč/hodnota pro daný klíč.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje prvky, které mají být odstraněny.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet hodnot přidružených k danému klíči.

### <a name="remarks"></a>Poznámky

`RemoveKey`odstraní všechny prvky klíč/hodnota, které mají klíč, který odpovídá *klíči*.

Informace o dalších dostupných metodách naleznete v dokumentaci k základní třídě [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Příklad

Viz příklad [crbmultimap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Viz také

[Třída CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Třída CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Třída CRBMap](../../atl/reference/crbmap-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
