---
title: Platform::Collections::Map – třída
ms.date: 10/01/2019
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
ms.openlocfilehash: 7f41a924811be95160b06a2097db6103cde8fc11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354451"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map – třída

Představuje *mapu*, což je kolekce párů klíč hodnota. Implementuje [Windows::Foundation::Collections::IObservableMap,](/uwp/api/windows.foundation.collections.iobservablemap_k_v_) který vám pomůže s [datovou vazbou](/windows/uwp/data-binding/data-binding-in-depth)XAML .

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
Typ, který poskytuje objekt funkce, který může porovnat dva hodnoty elementu jako klíče řazení k určení jejich relativní pořadí v mapě. Ve výchozím nastavení [\<std::less K>](../standard-library/less-struct.md).

*__is_valid_winrt_type()* Funkce generovaná kompilátorem, která ověřuje typ *K* a *V* a poskytuje popisnou chybovou zprávu, pokud typ nelze uložit do mapy.

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

- celá čísla

- třída rozhraní^

- veřejné ref třídy^

- hodnota struktura

- třída veřejného výčtu

Mapa je v podstatě obálka pro [std::map](../standard-library/map-class.md). Jedná se o konkrétní implementaci [jazyka Windows::Foundation::Collections::IMap<Windows::Foundation::Collections::IKeyValuePair\<K,V>>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) a [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, které jsou předávány přes veřejné rozhraní prostředí Windows Runtime. Pokud se pokusíte `Platform::Collections::Map` použít typ ve veřejné vrácené hodnotě nebo parametru, je vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou typu parametru nebo vrácené hodnoty [systému Windows::Foundation::Collections::IMap\<K,V>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Další informace naleznete v [tématu Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Mapa::Mapa](#ctor)|Inicializuje novou instanci třídy Map.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Mapa::Vymazat](#clear)|Odebere všechny dvojice klíč-hodnota z aktuálního objektu Map.|
|[Mapa::První](#first)|Vrátí iterátor, který určuje první prvek v mapě.|
|[Mapa::GetView](#getview)|Vrátí zobrazení aktuální mapy jen pro čtení. to znamená [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Mapa::Haskey](#haskey)|Určuje, zda aktuální mapa obsahuje zadaný klíč.|
|[Mapa::Vložit](#insert)|Přidá zadaný pár klíč-hodnota k aktuálnímu objektu Map.|
|[Mapa::Vyhledávání](#lookup)|Načte prvek na zadaný klíč v aktuální mapový objekt.|
|[Mapa::Odebrat](#remove)|Odstraní zadaný pár klíč-hodnota z aktuálního objektu Map.|
|[Mapa::Velikost](#size)|Vrátí počet prvků v aktuálním objektu Map.|

### <a name="events"></a>Události

|||
|-|-|
|Name (Název)|Popis|
|[Mapa::Událost MapChanged](#mapchanged)|Vyvolá se při změně mapy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Map`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="mapclear-method"></a><a name="clear"></a>Mapa::Vymazat metodu

Odebere všechny dvojice klíč-hodnota z aktuálního objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Mapa::První metoda

Vrátí iterátor, který určuje první prvek v `nullptr` mapě nebo pokud je mapa prázdná.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v mapě.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak podržet iterátor vrácený First() je přiřadit vrácenou hodnotu proměnné, která je deklarována s klíčovým slovem **automatického** odpočtu typu. Například, `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a>Mapa::Metoda GetView

Vrátí zobrazení aktuální mapy jen pro čtení. to znamená [platforma::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md), která implementuje rozhraní [Windows::Foundation::Collections::IMapView\<K,V>]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

Objekt. `MapView`

## <a name="maphaskey-method"></a><a name="haskey"></a>Mapa::Metoda Haskey

Určuje, zda aktuální mapa obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč použitý k vyhledání prvku Map. Typ *klíče* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je nalezen klíč; jinak **false**.

## <a name="mapinsert-method"></a><a name="insert"></a>Mapa::Metoda vložení

Přidá zadaný pár klíč-hodnota k aktuálnímu objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíččást dvojice klíč hodnota. Typ *klíče* je typename *K*.

*Hodnotu*<br/>
Část hodnoty dvojice klíč hodnota. Typ *hodnoty* je typename *V*.

### <a name="return-value"></a>Návratová hodnota

**true** pokud klíč existujícího prvku v aktuální mapě odpovídá *klíči* a hodnota části tohoto prvku je nastavena na *hodnotu*. **false,** pokud žádný existující prvek v aktuální mapě odpovídá *klíči* a parametry *klíče* a *hodnoty* jsou provedeny do páru klíč-hodnota a poté přidány do aktuální mapy.

## <a name="maplookup-method"></a><a name="lookup"></a>Mapa::Metoda vyhledávání

Načte hodnotu typu V, která je přidružena k zadanému klíči typu K, pokud klíč existuje.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč použitý k vyhledání prvku v mapě. Typ *klíče* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která je spárována s *klíčem*. Typ vrácené hodnoty je typename *V*.

### <a name="remarks"></a>Poznámky

Pokud klíč neexistuje, je [vyvolána platforma::OutOfBoundsException.](../cppcx/platform-outofboundsexception-class.md)

## <a name="mapmap-constructor"></a><a name="ctor"></a>Mapa::Konstruktor mapy

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

*Init*<br/>
Název typu aktuální mapy.

*Comp*<br/>
Typ, který poskytuje objekt funkce, který může porovnat dva hodnoty elementu jako klíče řazení k určení jejich relativní pořadí v mapě.

*M*<br/>
Odkaz nebo [rvalue,](../cpp/lvalues-and-rvalues-visual-cpp.md) `map Class` který se používá k inicializaci aktuální Map.

*První*<br/>
Vstupní iterátor prvního prvku v rozsahu prvků použitých k inicializaci aktuální mapy.

*Poslední*<br/>
Vstupní iterátor prvního prvku po rozsahu prvků použitých k inicializaci aktuální mapy.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Mapa::Událost změněné mapou

Je aktivována, když je položka vložena do mapy nebo odebrána z mapy.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

[A MapChangedEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler) který obsahuje informace o objektu, který vyvolal událost a druh změny, ke které došlo. Viz také [\<IMapChangedEventArgs K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) a [CollectionChange Výčet](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Ekvivalent v rozhraní .NET Framework

Aplikace prostředí Windows Runtime, které používají\<c# nebo visual basic\<projekt IMap K,V> jako IDictionary K,V>.

## <a name="mapremove-method"></a><a name="remove"></a>Mapa::Odebrat metodu

Odstraní zadaný pár klíč-hodnota z aktuálního objektu Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíččást dvojice klíč hodnota. Typ *klíče* je typename *K*.

## <a name="mapsize-method"></a><a name="size"></a>Mapa::Metoda velikosti

Vrátí počet [prvků systému Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) prvků v mapě.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v mapě.

## <a name="see-also"></a>Viz také

[Kolekce (C++/CX)](collections-c-cx.md)<br/>
[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření součástí prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
