---
title: 'Platform::Collections:: unorderedmap – třída | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fbc1905023f64c4983cf041eda244b28ce507abc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

*K*  
Typ klíče v dvojice klíč hodnota.

*V*  
Typ hodnoty v páru klíč / hodnota.

*C*  
Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v mapě. Ve výchozím nastavení [std::equal_to\<kB >](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

- celá čísla

- Třída rozhraní ^

- Třída veřejné ref ^

- Hodnota – struktura

- Veřejný výčet tříd

**UnorderedMap** je v podstatě obálka pro [std::unordered_map](../standard-library/unordered-map-class.md) úložiště typy prostředí Windows Runtime, která podporuje. Je konkrétní implementaci [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) a [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, které se předávají mezi veřejné rozhraní prostředí Windows Runtime. Pokud se pokusíte použít `Platform::Collections::UnorderedMap` zadejte veřejný návratovou hodnotu nebo parametru, je vyvolána C3986 Chyba kompilátoru. Můžete opravte chybu tak, že změníte typ hodnoty parametru nebo return k [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Inicializuje novou instanci třídy Map.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Unorderedmap::clear –](#clear)|Odebere všechny páry klíč hodnota z aktuálního objektu mapy.|
|[Unorderedmap::First –](#first)|Vrátí iterátor, který určuje první prvek v mapě.|
|[UnorderedMap::GetView](#getview)|Vrátí aktuální mapy; zobrazení jen pro čtení To znamená, Platform::Collections:: unorderedmapview – třída.|
|[UnorderedMap::HasKey](#haskey)|Určuje, zda aktuální mapy obsahuje zadaný klíč.|
|[Unorderedmap::Insert –](#insert)|Přidá k aktuálnímu objektu mapování na zadaný pár klíč hodnota.|
|[UnorderedMap::Lookup](#lookup)|Načte element v zadaný klíč v aktuálním objektu mapy.|
|[Unorderedmap::Remove –](#remove)|Odstraní zadaný pár klíč hodnota z aktuálního objektu mapy.|
|[Unorderedmap::size –](#size)|Vrátí počet prvků v aktuálním objektu mapy.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|[Map::mapchanged –](#mapchanged) událostí|Nastane při změně mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`UnorderedMap`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections

## <a name="clear"></a>  Unorderedmap::clear – metoda

Odebere všechny páry klíč hodnota z aktuálního objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Unorderedmap::First – metoda

Vrátí iterátor, který určuje první [Windows::Foundation::Collections::IKeyValuePair\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) element v neuspořádaný mapy.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ 
   First();
```

### <a name="return-value"></a>Návratová hodnota

Iterator, která určuje první prvek v mapě.

### <a name="remarks"></a>Poznámky

Pohodlný způsob pro uložení iterator vrácený First() je přiřadit návratovou hodnotu proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myUnorderedMap->First();`.

## <a name="getview"></a>  Unorderedmap::getview – metoda

Vrátí zobrazení jen pro čtení aktuální UnorderedMap; To znamená [Platform::Collections:: unorderedmapview – třída](../cppcx/platform-collections-unorderedmapview-class.md) , která implementuje [Windows::Foundation::Collections::IMapView::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) rozhraní.

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

*Klíč*  
Klíč používaná k nalezení UnorderedMap elementu. Typ *klíč* je typename *tisíc*.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je nalezen klíč; v opačném `false`.

## <a name="insert"></a>  Unorderedmap::Insert – metoda

Přidá zadaný pár klíč hodnota s aktuálním objektem UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *tisíc*.

*value*  
Část hodnotu z dvojice klíč hodnota. Typ *hodnotu* je typename *V*.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud klíč existujícího elementu v aktuální mapu odpovídá *klíč* a hodnota část tohoto elementu je nastavena na *hodnotu*. `false` Pokud žádné existující elementy v aktuálním mapě *klíč* a *klíč* a *hodnotu* parametry provedou do pár klíč hodnota a pak přidá do aktuální UnorderedMap.

## <a name="lookup"></a>  Unorderedmap::Lookup – metoda

Načte hodnotu z typu V, který je přidružen k zadanému klíči typu K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Klíč používaná k nalezení element v UnorderedMap. Typ *klíč* je typename *tisíc*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která je spárován s *klíč*. Typ vrácené hodnoty je typename *V*.

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

Vyvolá, když je položka vložena do nebo odebrat z mapování.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

A [MapChangedEventHandler\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) obsahující informace o objektu, který vyvolá událost a na druhu změny, která došlo k chybě. Viz také [IMapChangedEventArgs\<kB >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) a [CollectionChange výčtu](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Aplikace Windows Runtime, že nám C# nebo Visual Basic projektu IMap\<tisíc, V > jako IDictionary\<tisíc, V >.

## <a name="remove"></a>  Unorderedmap::Remove – metoda

Odstraní zadaný pár klíč hodnota z objektu UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *tisíc*.

## <a name="size"></a>  Unorderedmap::size – metoda

Vrátí počet [Windows::Foundation::Collections::IKeyValuePair\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementů v UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v neuspořádaný mapování.

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

*Init –*  
Typename aktuální UnorderedMap.

*P*  
Objekt funkce, která můžete porovnat dva klíče k určení, zda jsou stejné. Použije se výchozí hodnota tohoto parametru [std::equal_to\<kB >](../standard-library/equal-to-struct.md).

*H*  
Objekt funkce, která vytvoří hodnotu hash pro klíče. Použije se výchozí hodnota tohoto parametru [hash třídy 1](../standard-library/hash-class.md) pro typy klíč, aby třídy podporuje.

*m*  
Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::unordered_map](../standard-library/unordered-map-class.md) používané k chybě při inicializaci aktuální UnorderedMap.

*IL* A [std::initializer_list](../standard-library/initializer-list-class.md) z [std::pair](../standard-library/pair-structure.md) objekty, které slouží k inicializaci mapy.

*první*  
Vstupní iteraci prvním elementem v rozsahu prvků použitý k inicializaci aktuální UnorderedMap.

*poslední*  
Vstupní iterator první elementu po celou řadu prvky používané k chybě při inicializaci aktuální UnorderedMap.

## <a name="see-also"></a>Viz také

[Namespace platformy](platform-namespace-c-cx.md)  
[Platform::Collections – obor názvů](../cppcx/platform-collections-namespace.md)  
[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)  
[Platform::Collections::UnorderedMapView – třída](../cppcx/platform-collections-unorderedmapview-class.md)  
[Kolekce](../cppcx/collections-c-cx.md)  
[Vytváření Windows Runtime komponent v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
