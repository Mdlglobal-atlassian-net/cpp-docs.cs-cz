---
title: 'Platform::Collections:: map – třída'
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: ce50290217c7c06e26f26fc50564d3e37c873157
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565279"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections:: map – třída

Představuje *mapy*, což je kolekce párů klíč hodnota.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíče v páru klíč hodnota.

*V*<br/>
Typ hodnoty v páru klíč hodnota.

*C*<br/>
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v objektu Map. Ve výchozím nastavení [std::less\<K >](../standard-library/less-struct.md).

*__is_valid_winrt_type()* vygenerovaný kompilátorem funkci, která ověřuje typu *K* a *V* a poskytuje uživatelsky přívětivou chybovou zprávu, pokud typ nelze ukládat v objektu Map.

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

- celá čísla

- Třída rozhraní ^

- Třída Public ref class ^

- Hodnota – struktura

- Veřejný výčet tříd

Mapa je v podstatě obálka pro [std::map](../standard-library/map-class.md). Je konkrétní implementaci C++ [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K, V >>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) a [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, které jsou předány přes veřejné rozhraní Windows Runtime. Pokud se pokusíte použít `Platform::Collections::Map` zadejte veřejné návratová hodnota nebo parametr, je vyvolána C3986 Chyba kompilátoru. Chybu můžete vyřešit změnou typu parametr nebo návratovou hodnotu pro [Windows::Foundation::Collections::IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[Map::map](#ctor)|Inicializuje novou instanci třídy Map.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[Map::clear](#clear)|Odebere všechny páry klíč hodnota z aktuálního objektu Map.|
|[Map::First](#first)|Vrátí iterátor, který určuje první prvek v objektu map.|
|[Map::GetView](#getview)|Vrátí zobrazení jen pro čtení do aktuální mapování To znamená [Platform::Collections:: mapview – třída](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Určuje, zda aktuální mapa obsahuje zadaný klíč.|
|[Map::Insert](#insert)|Přidá zadanou dvojici klíč hodnota do aktuálního objektu Map.|
|[Map::Lookup](#lookup)|Získá prvek na zadaný klíč v aktuálním objektu Map.|
|[Map::Remove](#remove)|Odstraní zadanou dvojici klíč hodnota z aktuálního objektu Map.|
|[Map::size](#size)|Vrátí počet prvků v aktuálním objektu Map.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|[Map::mapchanged –](#mapchanged) událostí|Nastane, pokud se změní na mapě.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Map`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="clear"></a>  Map::clear – metoda

Odebere všechny páry klíč hodnota z aktuálního objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Map::First – metoda

Vrátí iterátor, který určuje první prvek v objektu map, nebo `nullptr` Pokud mapa je prázdný.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v objektu map.

### <a name="remarks"></a>Poznámky

Praktický způsob uložení iterátorů vrácené First() je přiřadit návratovou hodnotu proměnné, která je deklarována s **automaticky** klíčovým slovem odvození typu. Například, `auto x = myMap->First();`.

## <a name="getview"></a>  Map::GetView – metoda

Vrátí zobrazení jen pro čtení do aktuální mapování To znamená, [Platform::Collections:: mapview – třída](../cppcx/platform-collections-mapview-class.md), která implementuje [Windows::Foundation::Collections::IMapView\<K, V >] / uwp/api/Windows.Foundation.Collections.IMapView_K_V_) rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

A `MapView` objektu.

## <a name="haskey"></a>  Map::HasKey – metoda

Určuje, zda aktuální mapa obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč používaná k nalezení elementu mapy. Typ *klíč* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je klíč nalezen, jinak **false**.

## <a name="insert"></a>  Map::Insert – metoda

Přidá zadanou dvojici klíč hodnota do aktuálního objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *K*.

*value*<br/>
Hodnota část páru klíč hodnota. Typ *hodnotu* je typename *V*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud klíč existujícího prvku v aktuální mapování odpovídá *klíč* a hodnota část tohoto prvku je nastavená na *hodnota*. **false** žádné stávající elementy v aktuálním Map *klíč* a *klíč* a *hodnotu* parametry jsou provedeny v páru klíč hodnota a pak přidá do aktuální mapování.

## <a name="lookup"></a>  Map::Lookup – metoda

Načte hodnotu typu V, který je spojen se zadaným klíčem typu kB, pokud klíč existuje.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč používaná k nalezení prvku v objektu Map. Typ *klíč* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která se páruje s oblastí *klíč*. Typ vrácené hodnoty je typename *V*.

### <a name="remarks"></a>Poznámky

Pokud klíč neexistuje, o [Platform::outofboundsexception –](../cppcx/platform-outofboundsexception-class.md) je vyvolána výjimka.

## <a name="ctor"></a>  Map::map konstruktor

Inicializuje novou instanci třídy Map.

### <a name="syntax"></a>Syntaxe

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>Parametry

*Inicializace*<br/>
Typename aktuální mapování.

*comp*<br/>
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v objektu Map.

*m*<br/>
Odkaz nebo [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k `map Class` , který slouží k inicializaci aktuální mapování.

*první*<br/>
Vstupní iterátor první prvek v rozsahu prvků, které slouží k inicializaci aktuální mapování.

*last*<br/>
Vstupní iterátor první prvek po celou řadu prvků, které slouží k inicializaci aktuální mapování.

## <a name="mapchanged"></a>  Map::mapchanged – událost

Vyvoláno, když je položka vložena do nebo odebrány z mapy.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

A [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) , který obsahuje informace o objektu, který vyvolal událost a druh změn, ke které došlo. Viz také [IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) a [CollectionChange výčet](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Projekt aplikace Windows Runtime pomocí jazyka C# nebo Visual Basic IMap\<K, V > jako IDictionary\<K, V >.

## <a name="remove"></a>  Map::Remove – metoda

Odstraní zadanou dvojici klíč hodnota z aktuálního objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *K*.

## <a name="size"></a>  Map::size – metoda

Vrátí počet [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) prvků v objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v objektu Map.

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)<br/>
[Vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
