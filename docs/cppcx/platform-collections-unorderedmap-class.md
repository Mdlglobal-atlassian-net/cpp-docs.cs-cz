---
title: Platform::Collections::UnorderedMap – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 7790b363ef3f30b0ad0602568190ab443a2c1401
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423609"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap – třída

Představuje Neseřazený *mapy*, což je kolekce párů klíč hodnota.

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
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v objektu Map. Ve výchozím nastavení [std::equal_to\<K >](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

- celá čísla

- Třída rozhraní ^

- Třída Public ref class ^

- Hodnota – struktura

- Veřejný výčet tříd

**UnorderedMap** je v podstatě obálka pro [std::unordered_map](../standard-library/unordered-map-class.md) , který podporuje úložiště typy Windows Runtime. Je konkrétní implementaci [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) a [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, které jsou předány přes veřejné rozhraní Windows Runtime. Pokud se pokusíte použít `Platform::Collections::UnorderedMap` zadejte veřejné návratová hodnota nebo parametr, je vyvolána C3986 Chyba kompilátoru. Chybu můžete vyřešit změnou typu parametr nebo návratovou hodnotu pro [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Inicializuje novou instanci třídy Map.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|Odebere všechny páry klíč hodnota z aktuálního objektu Map.|
|[Unorderedmap::First –](#first)|Vrátí iterátor, který určuje první prvek v objektu map.|
|[UnorderedMap::GetView](#getview)|Vrátí zobrazení jen pro čtení do aktuální mapování To znamená, Platform::Collections:: unorderedmapview – třída.|
|[UnorderedMap::HasKey](#haskey)|Určuje, zda aktuální mapa obsahuje zadaný klíč.|
|[UnorderedMap::Insert](#insert)|Přidá zadanou dvojici klíč hodnota do aktuálního objektu Map.|
|[UnorderedMap::Lookup](#lookup)|Získá prvek na zadaný klíč v aktuálním objektu Map.|
|[Unorderedmap::Remove –](#remove)|Odstraní zadanou dvojici klíč hodnota z aktuálního objektu Map.|
|[Unorderedmap::size –](#size)|Vrátí počet prvků v aktuálním objektu Map.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|[Map::mapchanged –](#mapchanged) událostí|Nastane, pokud se změní na mapě.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`UnorderedMap`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="clear"></a>  Unorderedmap::clear – metoda

Odebere všechny páry klíč hodnota z aktuálního objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Unorderedmap::First – metoda

Vrátí iterátor, který určuje první [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) prvek neuspořádanou mapu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v objektu map.

### <a name="remarks"></a>Poznámky

Praktický způsob uložení iterátorů vrácené First() je přiřadit návratovou hodnotu proměnné, která je deklarována s **automaticky** klíčovým slovem odvození typu. Například, `auto x = myUnorderedMap->First();`.

## <a name="getview"></a>  Unorderedmap::getview – metoda

Vrátí aktuální UnorderedMap; zobrazení jen pro čtení To znamená [Platform::Collections:: unorderedmapview – třída](../cppcx/platform-collections-unorderedmapview-class.md) , který implementuje [Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

`UnorderedMapView` Objektu.

## <a name="haskey"></a>  Unorderedmap::haskey – metoda

Určuje, zda aktuální UnorderedMap obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč používaná k nalezení UnorderedMap elementu. Typ *klíč* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je klíč nalezen, jinak **false**.

## <a name="insert"></a>  Unorderedmap::Insert – metoda

Přidá zadanou dvojici klíč hodnota s aktuálním objektem UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *K*.

*value*<br/>
Hodnota část páru klíč hodnota. Typ *hodnotu* je typename *V*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud klíč existujícího prvku v aktuální mapování odpovídá *klíč* a hodnota část tohoto prvku je nastavená na *hodnota*. **false** žádné stávající elementy v aktuálním Map *klíč* a *klíč* a *hodnotu* parametry jsou provedeny v páru klíč hodnota a pak přidá do aktuální UnorderedMap.

## <a name="lookup"></a>  Unorderedmap::Lookup – metoda

Načte hodnotu typu V, který je přidružený k zadanému klíči typ K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč používaná k nalezení prvku v UnorderedMap. Typ *klíč* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která se páruje s oblastí *klíč*. Typ vrácené hodnoty je typename *V*.

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

Vyvoláno, když je položka vložena do nebo odebrány z mapy.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

A [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) , který obsahuje informace o objektu, který vyvolal událost a druh změn, ke které došlo. Viz také [IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) a [CollectionChange výčet](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Aplikace Windows Runtime, že nám C# nebo Visual Basic projektu IMap\<K, V > jako IDictionary\<K, V >.

## <a name="remove"></a>  Unorderedmap::Remove – metoda

Odstraní zadanou dvojici klíč hodnota z objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *K*.

## <a name="size"></a>  Unorderedmap::size – metoda

Vrátí počet [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) prvky UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v Neuspořádanou mapu.

## <a name="ctor"></a>  Unorderedmap::unorderedmap – konstruktor

Inicializuje novou instanci třídy UnorderedMap.

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

*Inicializace*<br/>
Typename aktuální UnorderedMap.

*P*<br/>
Objekt funkce, který může porovnat dva klíče pro určení, jestli jsou shodné. Výchozí hodnota tohoto parametru [std::equal_to\<K >](../standard-library/equal-to-struct.md).

*H*<br/>
Objekt funkce, který vytvoří hodnotu hash klíčů. Výchozí hodnota tohoto parametru [hash třídy 1](../standard-library/hash-class.md) pro klíč typy, které podporuje třídu.

*m*<br/>
Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::unordered_map](../standard-library/unordered-map-class.md) , který slouží k inicializaci aktuální UnorderedMap.

*il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) z [std::pair](../standard-library/pair-structure.md) objekty, které slouží k inicializaci mapy.

*první*<br/>
Vstupní iterátor první prvek v rozsahu prvků, které slouží k inicializaci aktuální UnorderedMap.

*last*<br/>
Vstupní iterátor první prvek po celou řadu prvků, které slouží k inicializaci aktuální UnorderedMap.

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Collections – obor názvů](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView – třída](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Kolekce](../cppcx/collections-c-cx.md)<br/>
[Vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
