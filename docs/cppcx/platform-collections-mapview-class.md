---
title: 'Platform::Collections:: mapview – třída'
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
ms.openlocfilehash: 1e38865f1d43edac4fc895052f1ea1b5a54a34ab
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749253"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections:: mapview – třída

Představuje zobrazení jen pro čtení *mapy*, což je kolekce párů klíč hodnota.

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
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků klíče řazení pro určení jejich relativního pořadí v MapView. Ve výchozím nastavení [std::less\<K >](../standard-library/less-struct.md).

### <a name="remarks"></a>Poznámky

MapView je konkrétní implementaci C++ [Windows::Foundation::Collections::IMapView \<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) rozhraní, který je předán napříč binárním rozhraním aplikace (ABI). Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[MapView::MapView](#ctor)|Inicializuje novou instanci třídy MapView.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[MapView::First](#first)|Vrátí iterátor, který je inicializován na první prvek v zobrazení mapy.|
|[MapView::HasKey](#haskey)|Určuje, zda aktuální MapView obsahuje zadaný klíč.|
|[MapView::Lookup](#lookup)|Získá prvek na zadaný klíč v aktuálním objektu MapView.|
|[MapView::Size](#size)|Vrátí počet prvků v aktuálním objektu MapView.|
|[MapView::Split](#split)|Původní objekt MapView rozdělí na dva objekty MapView.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MapView`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="first"></a> MapView::First – metoda

Vrátí iterátor, který určuje první prvek v zobrazení mapy.

### <a name="syntax"></a>Syntaxe

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v zobrazení mapy.

### <a name="remarks"></a>Poznámky

Praktický způsob uložení iterátorů vrácené First() je přiřadit návratovou hodnotu proměnné, která je deklarována s **automaticky** klíčovým slovem odvození typu. Například, `auto x = myMapView->First();`.

## <a name="haskey"></a>  MapView::HasKey – metoda

Určuje, zda aktuální MapView obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč používaná k nalezení MapView elementu. Typ *klíč* je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je klíč nalezen, jinak **false**.

##  <a name="lookup"></a> MapView::Lookup – metoda

Načte hodnotu typu V, který je přidružený k zadanému klíči typ K.

### <a name="syntax"></a>Syntaxe

```
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč používaná k nalezení prvku v MapView. Typ `key` je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která se páruje s oblastí `key`. Typ vrácené hodnoty je typename *V*.

##  <a name="ctor"></a> MapView::MapView konstruktor

Inicializuje novou instanci třídy MapView.

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

*Inicializace*<br/>
Typename aktuální MapView.

*comp*<br/>
Objekt funkce, který může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí v MapView.

*m*<br/>
Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k `map Class` , který slouží k inicializaci aktuální MapView.

*první*<br/>
Vstupní iterátor první prvek v rozsahu prvků, které slouží k inicializaci aktuální MapView.

*last*<br/>
Vstupní iterátor první prvek po celou řadu prvků, které slouží k inicializaci aktuální MapView.

*il*<br/>
A [std::initializer_list < std::pair\<K, V >>](../standard-library/initializer-list-class.md) jehož prvky se vloží do MapView.

##  <a name="size"></a> MapView::Size – metoda

Vrátí počet prvků v aktuálním objektu MapView.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v aktuální MapView.

##  <a name="split"></a> MapView::Split – metoda

Aktuální objekt MapView rozdělí na dva objekty MapView. Tato metoda je nefunkční.

### <a name="syntax"></a>Syntaxe

```
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>Parametry

*firstPartition*<br/>
První část na původní objekt MapView.

*secondPartition*<br/>
Druhá část na původní objekt MapView.

### <a name="remarks"></a>Poznámky

Tato metoda není funkční; To nemá žádný účinek.

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)
