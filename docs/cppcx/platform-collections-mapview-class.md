---
title: Platform::Collections::MapView – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: a770b318d893b9e81bdf11a75c2b0b05c0a9979f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750611"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView – třída

Představuje zobrazení jen pro čtení do *mapy*, což je kolekce párů klíč hodnota.

## <a name="syntax"></a>Syntaxe

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíče v páru klíč hodnota.

*V*<br/>
Typ hodnoty v páru klíč hodnota.

*C*<br/>
Typ, který poskytuje objekt funkce, který může porovnat dva hodnoty elementu jako klíče řazení k určení jejich relativní pořadí v MapView. Ve výchozím nastavení [\<std::less K>](../standard-library/less-struct.md).

### <a name="remarks"></a>Poznámky

MapView je konkrétní c++ implementace [Windows::Foundation::Collections::IMapView \<K,V>](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) rozhraní, které je předáno přes binární rozhraní aplikace (ABI). Další informace naleznete v [tématu Kolekce (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[MapView::MapView](#ctor)|Inicializuje novou instanci Třídy MapView.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[MapView::První](#first)|Vrátí iterátor, který je inicializován na první prvek v zobrazení mapy.|
|[Zobrazení mapy::Haskey](#haskey)|Určuje, zda aktuální MapView obsahuje zadaný klíč.|
|[MapView::Vyhledávání](#lookup)|Načte prvek na zadaný klíč v aktuální mapview objektu.|
|[MapView::Velikost](#size)|Vrátí počet prvků v aktuálním objektu MapView.|
|[MapView::Rozdělit](#split)|Rozdělí původní MapView objekt do dvou MapView objekty.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MapView`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="mapviewfirst-method"></a><a name="first"></a>MapView::První metoda

Vrátí iterátor, který určuje první prvek v zobrazení mapy.

### <a name="syntax"></a>Syntaxe

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v zobrazení mapy.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak podržet iterátor vrácený First() je přiřadit vrácenou hodnotu proměnné, která je deklarována s klíčovým slovem **automatického** odpočtu typu. Například, `auto x = myMapView->First();`.

## <a name="mapviewhaskey-method"></a><a name="haskey"></a>MapView::Metoda Haskey

Určuje, zda aktuální MapView obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč slouží k vyhledání MapView element. Typ *klíče* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je nalezen klíč; jinak **false**.

## <a name="mapviewlookup-method"></a><a name="lookup"></a>MapView::Metoda vyhledávání

Načte hodnotu typu V, která je přidružena k zadanému klíči typu K.

### <a name="syntax"></a>Syntaxe

```
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč slouží k vyhledání prvku v MapView. Typ `key` je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která je `key`spárována s . Typ vrácené hodnoty je typename *V*.

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a>MapView::Konstruktor MapView

Inicializuje novou instanci Třídy MapView.

### <a name="syntax"></a>Syntaxe

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>Parametry

*Init*<br/>
Název typu aktuální MapView.

*Comp*<br/>
Objekt funkce, který můžete porovnat dva element hodnoty jako klíče řazení k určení jejich relativní pořadí v MapView.

*M*<br/>
Odkaz nebo [Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) na `map Class` který se používá k inicializaci aktuální MapView.

*První*<br/>
Vstupní iterátor prvního prvku v rozsahu prvků použitých k inicializaci aktuálního Zobrazení Mapy.

*Poslední*<br/>
Vstupní iterátor prvního prvku po rozsahu prvků použitých k inicializaci aktuálního Zobrazení Mapy.

*Il*<br/>
[Std::initializer_list<\<std::pair K,V>>](../standard-library/initializer-list-class.md) jehož prvky budou vloženy do MapView.

## <a name="mapviewsize-method"></a><a name="size"></a>MapView::Metoda velikosti

Vrátí počet prvků v aktuálním objektu MapView.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v aktuální mapview.

## <a name="mapviewsplit-method"></a><a name="split"></a>MapView::Metoda rozdělení

Rozdělí aktuální MapView objekt do dvou MapView objekty. Tato metoda není funkční.

### <a name="syntax"></a>Syntaxe

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>Parametry

*první oddíl*<br/>
První část původní MapView objektu.

*druhý oddíl*<br/>
Druhá část původní MapView objektu.

### <a name="remarks"></a>Poznámky

Tato metoda není funkční; to nedělá nic.

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
