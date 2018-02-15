---
title: "Třída Platform::Collections::map | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
dev_langs:
- C++
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e54750d02386795e46675b31a06a082bd35402f1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::map – třída

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

*K*  
 Typ klíče v dvojice klíč hodnota.

*V*  
Typ hodnoty v páru klíč / hodnota.

*C*  
Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v mapě. Ve výchozím nastavení [std::less\<kB >](../standard-library/less-struct.md).

*__is_valid_winrt_type()*  
Kompilátoru generované funkci, která ověří typ *tisíc* a *V* a poskytuje popisný chybovou zprávu, pokud typ nelze uložit v mapě.

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

- celá čísla

- Třída rozhraní ^

- Třída veřejné ref ^

- Hodnota – struktura

- Veřejný výčet tříd

Mapa je v podstatě obálka pro [std::map](../standard-library/map-class.md). Je konkrétní implementaci C++ [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<tisíc, V >>](http://go.microsoft.com/fwlink/p/?LinkId=262408) a [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) typy, které se předávají mezi veřejné rozhraní prostředí Windows Runtime. Pokud se pokusíte použít `Platform::Collections::Map` zadejte veřejný návratovou hodnotu nebo parametru, je vyvolána C3986 Chyba kompilátoru. Můžete opravte chybu tak, že změníte typ hodnoty parametru nebo return k [Windows::Foundation::Collections::IMap\<tisíc, V >](http://go.microsoft.com/fwlink/p/?LinkId=262408).

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Map::Map](#ctor)|Inicializuje novou instanci třídy Map.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Map::Clear](#clear)|Odebere všechny páry klíč hodnota z aktuálního objektu mapy.|
|[Map::First](#first)|Vrátí iterátor, který určuje první prvek v mapě.|
|[Map::GetView](#getview)|Vrátí aktuální mapy; zobrazení jen pro čtení To znamená [Platform::Collections::MapView třída](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Určuje, zda aktuální mapy obsahuje zadaný klíč.|
|[Map::Insert](#insert)|Přidá k aktuálnímu objektu mapování na zadaný pár klíč hodnota.|
|[Map::Lookup](#lookup)|Načte element v zadaný klíč v aktuálním objektu mapy.|
|[Map::Remove](#remove)|Odstraní zadaný pár klíč hodnota z aktuálního objektu mapy.|
|[Map::size](#size)|Vrátí počet prvků v aktuálním objektu mapy.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|[Map::mapchanged –](#mapchanged-event.md) `event`|Nastane při změně mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Map`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections

## <a name="clear"></a>  Map::clear – metoda

Odebere všechny páry klíč hodnota z aktuálního objektu mapy.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Map::First – metoda

Vrátí iterátor, který určuje první prvek v mapě, nebo `nullptr` Pokud mapy je prázdný.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterator, která určuje první prvek v mapě.

### <a name="remarks"></a>Poznámky

Pohodlný způsob pro uložení iterator vrácený First() je přiřadit návratovou hodnotu proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myMap->First();`.

## <a name="getview"></a>  Map::GetView – metoda

Vrátí aktuální mapy; zobrazení jen pro čtení To znamená [Platform::Collections::MapView třída](../cppcx/platform-collections-mapview-class.md), který implementuje [Windows::Foundation::Collections::IMapView\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

A `MapView` objektu.

## <a name="haskey"></a>  Map::HasKey – metoda

Určuje, zda aktuální mapy obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Klíč používaná k nalezení elementu mapy. Typ *klíč* je typename *tisíc*.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je nalezen klíč; v opačném `false`.

## <a name="insert"></a>  Map::Insert – metoda

Přidá k aktuálnímu objektu mapování na zadaný pár klíč hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *tisíc*.

*value*  
Část hodnotu z dvojice klíč hodnota. Typ *hodnotu* je typename *V*.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud klíč existujícího elementu v aktuální mapu odpovídá *klíč* a hodnota část tohoto elementu je nastavena na *hodnotu*. `false` Pokud žádné existující elementy v aktuálním mapě *klíč* a *klíč* a *hodnotu* parametry provedou do pár klíč hodnota a pak přidá do aktuální mapy.

## <a name="lookup"></a>  Map::Lookup – metoda

Načte hodnotu typu V, který je přidružen k zadanému klíči typu kB, pokud klíč existuje.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Klíč používaná k nalezení element v mapě. Typ *klíč* je typename *tisíc*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která je spárován s *klíč*. Typ vrácené hodnoty je typename *V*.

### <a name="remarks"></a>Poznámky

Pokud klíč neexistuje, pak [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) je vyvolána výjimka.

## <a name="ctor"></a>  Map::map – konstruktor

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

*Init –*  
Typename aktuální mapy.

*comp*  
Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v mapě.

*m*  
Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k `map Class` používané k chybě při inicializaci aktuální mapy.

*první*  
Vstupní iteraci prvním elementem v rozsahu prvků použitý k inicializaci aktuální mapy.

*last*  
Vstupní iterator první elementu po celou řadu prvky používané k chybě při inicializaci aktuální mapy.

## <a name="mapchanged"></a>  Map::mapchanged – událost

Vyvolá, když je položka vložena do nebo odebrat z mapování.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

A [MapChangedEventHandler\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) obsahující informace o objektu, který vyvolá událost a na druhu změny, která došlo k chybě. Viz také [IMapChangedEventArgs\<kB >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) a [CollectionChange výčtu](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Aplikace Windows Runtime, které používají C# nebo Visual Basic projektu IMap\<tisíc, V > jako IDictionary\<tisíc, V >.

## <a name="remove"></a>  Map::Remove – metoda

Odstraní zadaný pár klíč hodnota z aktuálního objektu mapy.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*Klíč*  
Část klíče dvojice klíč hodnota. Typ *klíč* je typename *tisíc*.

## <a name="size"></a>  Map::size – metoda

Vrátí počet [Windows::Foundation::Collections::IKeyValuePair\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) prvků v mapování.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v mapování.

## <a name="see-also"></a>Viz také

[Namespace platformy](platform-namespace-c-cx.md)  
[Vytváření Windows Runtime komponent v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
