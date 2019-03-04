---
title: Crbmultimap – třída
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
ms.openlocfilehash: 03a9639e8b0b3d11a414e5db0ce874d7ca8f2d45
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267482"
---
# <a name="crbmultimap-class"></a>Crbmultimap – třída

Tato třída reprezentuje strukturu mapování, která umožňuje že každému klíči je možné přidružit více než jednu hodnotu pomocí binárního stromu černé Red.

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
Typ klíče prvku.

*V*<br/>
Typ elementu hodnota.

*KTraits*<br/>
Kód použitý má zkopírovat nebo přesunout klíčové prvky. Zobrazit [celementtraits – třída](../../atl/reference/celementtraits-class.md) další podrobnosti.

*VTraits*<br/>
Kód použitý má zkopírovat nebo přesunout elementy hodnotu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Konstruktor|
|[CRBMultiMap::~CRBMultiMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Voláním této metody lze najít pozici prvního prvku k danému klíči.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Volejte tuto metodu za účelem získání hodnotu přidruženou k danému klíči a aktualizujte hodnotu pozice.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Volejte tuto metodu za účelem získání elementu přidružené k danému klíči a aktualizujte hodnotu pozice.|
|[CRBMultiMap::Insert](#insert)|Voláním této metody lze vložit páru prvek do objektu map.|
|[CRBMultiMap::RemoveKey](#removekey)|Volejte tuto metodu, která odebere všechny prvky klíč/hodnota pro zadaný klíč.|

## <a name="remarks"></a>Poznámky

`CRBMultiMap` poskytuje podporu pro mapování pole daného typu, Správa uspořádaného pole klíčové prvky a hodnot. Na rozdíl od [crbmap –](../../atl/reference/crbmap-class.md) třídy, každý klíč lze přidružit více než jednu hodnotu.

Prvky (skládající se z klíče a hodnoty) jsou uloženy v binárního stromu struktury, pomocí [CRBMultiMap::Insert](#insert) metody. Prvky lze odebrat prostřednictvím [CRBMultiMap::RemoveKey](#removekey) metoda, která odstraňuje všechny prvky, které odpovídají danému klíči.

Procházení stromu je možné provádět pomocí metod, jako [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), a [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Přístup k potenciálně více hodnot pro každý klíč je možné používat [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), a [CRBMultiMap::GetNextWithKey ](#getnextwithkey) metody. Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap) pro ilustraci tohoto v praxi.

*KTraits* a *VTraits* parametry jsou třídy, které obsahují žádný doplňkový kód potřeba zkopírovat nebo přesunout prvky.

`CRBMultiMap` je odvozen z [crbtree –](../../atl/reference/crbtree-class.md), který implementuje pomocí algoritmu Red černé binárního stromu. Alternativa k `CRBMultiMap` a `CRBMap` nabízí [catlmap –](../../atl/reference/catlmap-class.md) třídy. Pokud musí být uložen pouze malý počet prvků, zvažte použití [csimplemap –](../../atl/reference/csimplemap-class.md) namísto třídy.

Podrobnější diskuzi o různých třídy kolekcí a jejich funkce a výkonové charakteristiky, naleznete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap

Konstruktor

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Velikost bloku.

### <a name="remarks"></a>Poznámky

*NBlockSize* parametr je míra množství paměti přidělené, pokud je nutné použít nový prvek. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků. Výchozí hodnota se přidělit prostor pro 10 prvků v čase.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMultiMap::~CRBMultiMap

Destruktor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey

Voláním této metody lze najít pozici prvního prvku k danému klíči.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje elementu, který chcete najít.

### <a name="return-value"></a>Návratová hodnota

Vrátí POZICI prvního prvku klíč/hodnota, pokud je nalezen klíč, NULL jinak.

### <a name="remarks"></a>Poznámky

Klíč v `CRBMultiMap` může mít jednu nebo více přidružených hodnot. Tato metoda poskytne hodnota pozice první hodnoty (což ve skutečnosti může být jediná hodnota) přidružené k této konkrétní klíč. Vrácená hodnota pozice pak jde použít s [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) nebo [CRBMultiMap::GetNextWithKey](#getnextwithkey) k získání hodnoty a aktualizaci umístění.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey

Volejte tuto metodu za účelem získání hodnotu přidruženou k danému klíči a aktualizujte hodnotu pozice.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Hodnota pozice, získali buď voláním [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) nebo [CRBMultiMap::GetNextWithKey](#getnextwithkey), nebo předchozí volání k `GetNextValueWithKey`.

*key*<br/>
Určuje klíč, který identifikuje elementu, který chcete najít.

### <a name="return-value"></a>Návratová hodnota

Vrátí element pár spojené s daným klíčem.

### <a name="remarks"></a>Poznámky

Hodnota pozice je aktualizována tak, aby odkazoval na nejbližší hodnotu přiřazenou klíči. Pokud neexistují žádné další hodnoty pozice hodnota nastavená na hodnotu NULL.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey

Volejte tuto metodu za účelem získání elementu přidružené k danému klíči a aktualizujte hodnotu pozice.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Hodnota pozice, získali buď voláním [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) nebo [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), nebo předchozí volání k `GetNextWithKey`.

*key*<br/>
Určuje klíč, který identifikuje elementu, který chcete najít.

### <a name="return-value"></a>Návratová hodnota

Vrátí Další [CRBTree::CPair třídy](crbtree-class.md#cpair_class) element spojený s daným klíčem.

### <a name="remarks"></a>Poznámky

Hodnota pozice je aktualizována tak, aby odkazoval na nejbližší hodnotu přiřazenou klíči. Pokud neexistují žádné další hodnoty pozice hodnota nastavená na hodnotu NULL.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

##  <a name="insert"></a>  CRBMultiMap::Insert

Voláním této metody lze vložit páru prvek do objektu map.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnotu klíče pro přidání do `CRBMultiMap` objektu.

*value*<br/>
Hodnota k přidání do `CRBMultiMap` objekt přidružený k *klíč*.

### <a name="return-value"></a>Návratová hodnota

Vrátí pozici prvku dvojice klíč/hodnota v `CRBMultiMap` objektu.

### <a name="remarks"></a>Poznámky

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="removekey"></a>  CRBMultiMap::RemoveKey

Volejte tuto metodu, která odebere všechny prvky klíč/hodnota pro zadaný klíč.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Určuje klíč, který identifikuje elementy, která se má odstranit.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet hodnot, které jsou přidružené k danému klíči.

### <a name="remarks"></a>Poznámky

`RemoveKey` Odstraní všechny prvky klíč/hodnota, které mají klíč, který odpovídá *klíč*.

Najdete v dokumentaci pro základní třídu [crbtree –](../../atl/reference/crbtree-class.md) informace o dalších metodách, k dispozici.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Viz také:

[CRBTree – třída](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap – třída](../../atl/reference/catlmap-class.md)<br/>
[CRBMap – třída](../../atl/reference/crbmap-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
