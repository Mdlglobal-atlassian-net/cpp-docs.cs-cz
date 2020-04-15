---
title: Platform::Collections::UnorderedMap – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: c6f702850f5bf84b8b1bc857c9d0a744728d0cbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354418"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap – třída

Představuje neuspořádané *mapy*, což je kolekce párů klíč hodnota.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíče v páru klíč hodnota.

*V*<br/>
Typ hodnoty v páru klíč hodnota.

*C*<br/>
Typ, který poskytuje objekt funkce, který může porovnat dva hodnoty elementu jako klíče řazení k určení jejich relativní pořadí v mapě. Ve výchozím nastavení [\<std::equal_to K>](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

- celá čísla

- třída rozhraní^

- veřejné ref třídy^

- hodnota struktura

- třída veřejného výčtu

**UnorderedMap** je v podstatě obálka pro [std::unordered_map,](../standard-library/unordered-map-class.md) která podporuje ukládání typů prostředí Windows Runtime. Jedná se o konkrétní implementaci [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) a [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, které jsou předávány přes veřejné rozhraní prostředí Windows Runtime. Pokud se pokusíte `Platform::Collections::UnorderedMap` použít typ ve veřejné vrácené hodnotě nebo parametru, je vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou typu parametru nebo vrácené hodnoty [systému Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Další informace naleznete v [tématu Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Inicializuje novou instanci třídy Map.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[UnorderedMap::Vymazat](#clear)|Odebere všechny dvojice klíč-hodnota z aktuálního objektu Map.|
|[UnorderedMap::První](#first)|Vrátí iterátor, který určuje první prvek v mapě.|
|[UnorderedMap::GetView](#getview)|Vrátí zobrazení aktuální mapy jen pro čtení. to znamená Platform::Collections::UnorderedMapView Class.|
|[UnorderedMap::HasKey](#haskey)|Určuje, zda aktuální mapa obsahuje zadaný klíč.|
|[UnorderedMap::Vložit](#insert)|Přidá zadaný pár klíč-hodnota k aktuálnímu objektu Map.|
|[UnorderedMap::Vyhledávání](#lookup)|Načte prvek na zadaný klíč v aktuální mapový objekt.|
|[UnorderedMap::Odebrat](#remove)|Odstraní zadaný pár klíč-hodnota z aktuálního objektu Map.|
|[UnorderedMap::Velikost](#size)|Vrátí počet prvků v aktuálním objektu Map.|

### <a name="events"></a>Události

|||
|-|-|
|Name (Název)|Popis|
|[Mapa::Událost MapChanged](#mapchanged)|Vyvolá se při změně mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`UnorderedMap`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="unorderedmapclear-method"></a><a name="clear"></a>UnorderedMap::Vymazat metodu

Odebere všechny dvojice klíč-hodnota z aktuálního objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>UnorderedMap::První metoda

Vrátí iterátor, který určuje první [prvek Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) prvek v neuspořádané mapě.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v mapě.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak podržet iterátor vrácený First() je přiřadit vrácenou hodnotu proměnné, která je deklarována s klíčovým slovem **automatického** odpočtu typu. Například, `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>UnorderedMap::Metoda GetView

Vrátí zobrazení pro čtení aktuální hodu Neuspořádané mapy. to znamená [platforma::Collections::UnorderedMapView Class,](../cppcx/platform-collections-unorderedmapview-class.md) která implementuje rozhraní [Windows::Foundation::Collections::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `UnorderedMapView`.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap::Metoda HasKey

Určuje, zda aktuální UnorderedMap obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč slouží k vyhledání UnorderedMap element. Typ *klíče* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je nalezen klíč; jinak **false**.

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>UnorderedMap::Metoda vložení

Přidá zadaný pár klíč-hodnota k aktuálnímu objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíččást dvojice klíč hodnota. Typ *klíče* je typename *K*.

*Hodnotu*<br/>
Část hodnoty dvojice klíč hodnota. Typ *hodnoty* je typename *V*.

### <a name="return-value"></a>Návratová hodnota

**true** pokud klíč existujícího prvku v aktuální mapě odpovídá *klíči* a hodnota části tohoto prvku je nastavena na *hodnotu*. **false,** pokud žádný existující prvek v aktuální mapě odpovídá *klíč* a *parametry klíč* a *hodnota* jsou provedeny do dvojice klíč-hodnota a pak přidány do aktuální UnorderedMap.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>UnorderedMap::Metoda vyhledávání

Načte hodnotu typu V, která je přidružena k zadanému klíči typu K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč slouží k vyhledání prvku v UnorderedMap. Typ *klíče* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která je spárována s *klíčem*. Typ vrácené hodnoty je typename *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>UnorderedMap::MapaZměněná

Je aktivována, když je položka vložena do mapy nebo odebrána z mapy.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

[A MapChangedEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler) který obsahuje informace o objektu, který vyvolal událost a druh změny, ke které došlo. Viz také [\<IMapChangedEventArgs K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) a [CollectionChange Výčet](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Aplikace prostředí Windows Runtime, které nám\<c# nebo visual basic\<projektu IMap K,V> jako IDictionary K,V>.

## <a name="unorderedmapremove-method"></a><a name="remove"></a>UnorderedMap::Odebrat metodu

Odstraní zadaný pár klíč-hodnota z objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíččást dvojice klíč hodnota. Typ *klíče* je typename *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a>UnorderedMap::Metoda velikosti

Vrátí počet [windows::foundation::collections::iKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) prvky v UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v neuspořádané mapě.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap::Konstruktor UnorderedMap

Inicializuje novou instanci unorderedmap třídy.

### <a name="syntax"></a>Syntaxe

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>Parametry

*Init*<br/>
Název typu aktuální UnorderedMap.

*P*<br/>
Objekt funkce, který můžete porovnat dva klíče k určení, zda jsou stejné. Tento parametr je výchozí [pro\<std::equal_to K>](../standard-library/equal-to-struct.md).

*H*<br/>
Objekt funkce, který vytváří hodnotu hash pro klíče. Tento parametr je výchozí [pro hash Class 1](../standard-library/hash-class.md) pro typy klíčů, které třída podporuje.

*M*<br/>
Odkaz nebo [Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) na [std::unordered_map,](../standard-library/unordered-map-class.md) který se používá k inicializaci aktuální UnorderedMap.

*Il*<br/>
[Std::initializer_list](../standard-library/initializer-list-class.md) [std::pair](../standard-library/pair-structure.md) objekty, které slouží k inicializaci mapy.

*První*<br/>
Vstupní iterátor prvního prvku v rozsahu prvků použitých k inicializaci aktuální unorderedMap.

*Poslední*<br/>
Vstupní iterátor prvního prvku po rozsahu prvků použitých k inicializaci aktuální unorderedMap.

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Platforma::Obor názvů kolekcí](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView – třída](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Kolekce](../cppcx/collections-c-cx.md)<br/>
[Vytváření součástí prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
