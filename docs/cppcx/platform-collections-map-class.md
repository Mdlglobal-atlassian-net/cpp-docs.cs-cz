---
title: 'Platform:: Collections:: map – třída'
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
ms.openlocfilehash: 81721d719a424250beed89f4a5656b3f2fc27922
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816301"
---
# <a name="platformcollectionsmap-class"></a>Platform:: Collections:: map – třída

Představuje *mapu*, která je kolekcí párů klíč-hodnota. Implementuje [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap_k_v_) pro usnadnění [vazby dat](/windows/uwp/data-binding/data-binding-in-depth)XAML.

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
Typ klíče v páru klíč-hodnota.

*ICES*<br/>
Typ hodnoty v páru klíč-hodnota.

*C*<br/>
Typ, který poskytuje objekt funkce, který může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí v mapě. Ve výchozím nastavení je [> std:: less @ no__t-1 tisíc](../standard-library/less-struct.md).

*__is_valid_winrt_type ()* Funkce vygenerovaná kompilátorem, která ověřuje typ *K* a *V* a poskytuje popisnou chybovou zprávu, pokud typ nemůže být uložen na mapě.

### <a name="remarks"></a>Poznámky

Povolené typy:

- Celá čísla

- Třída rozhraní ^

- Třída Public ref class ^

- struktura hodnoty

- Public enum – třída

Mapa je v podstatě obálkou pro [std:: map](../standard-library/map-class.md). Jedná se o C++ konkrétní implementaci [Windows:: Foundation:: Collections:: IMAP < Windows:: Foundation:: Collections:: IKeyValuePair @ no__t-2K, V > >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) a [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) typy, které se předávají přes veřejná okna. Běhová rozhraní. Pokud se pokusíte použít typ `Platform::Collections::Map` ve veřejné návratové hodnotě nebo parametru, je vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou typu parametru nebo návratové hodnoty na [Windows:: Foundation:: Collections:: IMAP @ no__t-1 tisíc, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="members"></a>Pedagog

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Map:: map](#ctor)|Inicializuje novou instanci třídy map.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Map:: Clear](#clear)|Odebere všechny páry klíč-hodnota z aktuálního objektu mapy.|
|[Map:: First](#first)|Vrátí iterátor, který určuje první prvek v mapě.|
|[Map:: GetView](#getview)|Vrátí zobrazení aktuálního mapování jen pro čtení. To znamená, že [Třída Platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md).|
|[Map:: Haskey –](#haskey)|Určuje, zda aktuální mapa obsahuje zadaný klíč.|
|[Map:: INSERT](#insert)|Přidá k aktuálnímu objektu mapy zadanou dvojici klíč-hodnota.|
|[Map:: Lookup](#lookup)|Načte prvek v zadaném klíči v aktuálním objektu map.|
|[Map:: Remove](#remove)|Odstraní specifikovanou dvojici klíč-hodnota z aktuálního objektu mapy.|
|[Map:: size](#size)|Vrátí počet prvků v aktuálním objektu map.|

### <a name="events"></a>Akce

|||
|-|-|
|Name (Název)|Popis|
|[Map:: MapChanged –](#mapchanged) událost|Nastane, pokud se změní mapa.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Map`

### <a name="requirements"></a>Požadavky

**Header:** Collection. h

**Obor názvů:** Platform:: Collections

## <a name="clear"></a>Map:: Clear – metoda

Odebere všechny páry klíč-hodnota z aktuálního objektu mapy.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>Map:: First – metoda

Vrátí iterátor, který určuje první prvek v mapě, nebo `nullptr`, pokud je mapa prázdná.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v mapě.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak uchovávat iterátory vrácené funkcí First (), je přiřadit návratovou hodnotu proměnné, která je deklarována s klíčovým slovem srážky typu **auto** . Například, `auto x = myMap->First();`.

## <a name="getview"></a>Map:: GetView – metoda

Vrátí zobrazení aktuálního mapování jen pro čtení. To znamená, že [Třída Platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md), která implementuje rozhraní [Windows:: Foundation:: Collections:: IMapView @ No__t-1 tisíc, V >]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `MapView`.

## <a name="haskey"></a>Map:: Haskey – – metoda

Určuje, zda aktuální mapa obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč, který slouží k vyhledání mapového prvku. Typ *klíče* je TypeName *K*.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se klíč najde; v opačném případě **false**.

## <a name="insert"></a>Map:: Insert – metoda

Přidá k aktuálnímu objektu mapy zadanou dvojici klíč-hodnota.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíčová část páru klíč-hodnota. Typ *klíče* je TypeName *K*.

*value*<br/>
Část hodnoty páru klíč-hodnota. Typ *hodnoty* je TypeName *V*.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud klíč stávajícího prvku v aktuální mapě odpovídá *klíči* a hodnota části tohoto prvku je nastavena na *hodnotu*. **false** , pokud žádný existující element v aktuální mapě neodpovídá *klíči* a parametry *klíče* a *hodnoty* se provedou s dvojicí klíč-hodnota a pak se přidaly k aktuální mapě.

## <a name="lookup"></a>Map:: Lookup – Metoda

Načte hodnotu typu V, která je přidružena k zadanému klíči typu K, pokud klíč existuje.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč, který slouží k vyhledání prvku v mapě. Typ *klíče* je TypeName *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která se spáruje s *klíčem*. Typ návratové hodnoty je TypeName *V*.

### <a name="remarks"></a>Poznámky

Pokud klíč neexistuje, je vyvolána výjimka [Platform:: OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) .

## <a name="ctor"></a>Map:: map – konstruktor

Inicializuje novou instanci třídy map.

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

*For*<br/>
Název TypeName aktuální mapy

*zajištění*<br/>
Typ, který poskytuje objekt funkce, který může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí v mapě.

*4m*<br/>
Odkaz nebo [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) na `map Class`, které se používají k inicializaci aktuální mapy.

*první*<br/>
Vstupní iterátor prvního prvku v rozsahu prvků, který slouží k inicializaci aktuální mapy.

*posledního*<br/>
Vstupní iterátor prvního prvku za rozsah prvků použitý k inicializaci aktuální mapy.

## <a name="mapchanged"></a>Map:: MapChanged – událost

Je aktivována při vložení nebo odebrání položky z mapy.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

[MapChangedEventHandler @ no__t-1 tisíc, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) , který obsahuje informace o objektu, který vyvolal událost, a o druhu změny, ke které došlo. Viz také [IMapChangedEventArgs @ no__t-1 tisíc >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) a [CollectionChange](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Ekvivalent .NET Framework

Prostředí Windows Runtime aplikace, které C# používají nebo Visual Basic Project IMAP @ No__t-1 tisíc, v > jako IDictionary @ No__t-2k, v >.

## <a name="remove"></a>Map:: Remove – metoda

Odstraní specifikovanou dvojici klíč-hodnota z aktuálního objektu mapy.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíčová část páru klíč-hodnota. Typ *klíče* je TypeName *K*.

## <a name="size"></a>Map:: size – metoda

Vrátí počet elementů [Windows:: Foundation:: Collections:: IKeyValuePair @ no__t-1 tisíc, v >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) v mapě.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v mapě.

## <a name="see-also"></a>Další informace najdete v tématech

[Kolekce (C++/CX)](collections-c-cx.md)<br/>
[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření komponent prostředí Windows Runtime v nástrojiC++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
