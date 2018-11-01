---
title: Platform::Collections::UnorderedMapView – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: 9564904fa77ae6a7355119e83bdfa3ac65a4050c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560833"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView – třída

Představuje zobrazení jen pro čtení *mapy*, což je kolekce párů klíč hodnota.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíče v páru klíč hodnota.

*V*<br/>
Typ hodnoty v páru klíč hodnota.

*C*<br/>
Typ poskytující objekt funkce, který může porovnat dva klíče hodnoty na rovnost. Ve výchozím nastavení [std::equal_to\<K >](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Poznámky

UnorderedMapView je konkrétní implementaci C++ [Windows::Foundation::Collections::IMapView\<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) rozhraní, který je předán napříč binárním rozhraním aplikace (ABI). Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|Inicializuje novou instanci třídy UnorderedMapView.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Unorderedmapview::First –](#first)|Vrátí iterátor, který je inicializován na první prvek v zobrazení mapy.|
|[UnorderedMapView::HasKey](#haskey)|Určuje, zda aktuální UnorderedMapView obsahuje zadaný klíč.|
|[UnorderedMapView::Lookup](#lookup)|Získá prvek na zadaný klíč v aktuálním objektu UnorderedMapView.|
|[Unorderedmapview::size –](#size)|Vrátí počet prvků v aktuálním objektu UnorderedMapView.|
|[Unorderedmapview::split –](#split)|Původní objekt UnorderedMapView rozdělí na dva objekty UnorderedMapView.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`UnorderedMapView`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="first"></a>  Unorderedmapview::First – metoda

Vrátí iterátor, který určuje první [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) prvek neuspořádanou mapu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v zobrazení mapy.

### <a name="remarks"></a>Poznámky

Praktický způsob uložení iterátorů vrácené First() je přiřadit návratovou hodnotu proměnné, která je deklarována s **automaticky** klíčovým slovem odvození typu. Například `auto x = myMapView->First();`.

## <a name="haskey"></a>  Unorderedmapview::haskey – metoda

Určuje, zda aktuální UnorderedMap obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč používaná k nalezení prvku. Typ `key` je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je klíč nalezen, jinak **false**.

## <a name="lookup"></a>  Unorderedmapview::Lookup – metoda

Načte hodnotu typu V, který je přidružený k zadanému klíči typ K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč používaná k nalezení prvku v UnorderedMapView. Typ `key` je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která se páruje s oblastí `key`. Typ vrácené hodnoty je typename *V*.

## <a name="size"></a>  Unorderedmapview::size – metoda

Vrátí počet [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) prvky UnorderedMapView.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v Neseřazený MapView.

## <a name="split"></a>  Unorderedmapview::split – metoda

Aktuální objekt UnorderedMapView rozdělí na dva objekty UnorderedMapView. Tato metoda je nefunkční.

### <a name="syntax"></a>Syntaxe

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>Parametry

*firstPartition*<br/>
První část na původní objekt UnorderedMapView.

*secondPartition*<br/>
Druhá část na původní objekt UnorderedMapView.

### <a name="remarks"></a>Poznámky

Tato metoda není funkční; To nemá žádný účinek.

## <a name="ctor"></a>  Unorderedmapview::unorderedmapview – konstruktor

Inicializuje novou instanci třídy UnorderedMapView.

### <a name="syntax"></a>Syntaxe

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>Parametry

*n*<br/>
Počet prvků, které se předem přidělte místo pro.

*Inicializace*<br/>
Typename UnorderedMapView.

*H*<br/>
Objekt funkce, která se dá hodnotu hash pro klíč. Výchozí hodnota je [std::hash\<K >](../standard-library/hash-class.md) pro typy, které `std::hash` podporuje.

*P*<br/>
Typ poskytující objekt funkce, který může porovnat dva klíče pro určení jejich rovnosti. Výchozí hodnota je [std::equal_to\<K >](../standard-library/equal-to-struct.md).

*m*<br/>
Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::unordered_map](../standard-library/unordered-map-class.md) , který slouží k inicializaci UnorderedMapView.

*první*<br/>
Vstupní iterátor první prvek v rozsahu prvků, které slouží k inicializaci UnorderedMapView.

*poslední*<br/>
Vstupní iterátor první prvek po celou řadu prvků, které slouží k inicializaci UnorderedMapView.

## <a name="see-also"></a>Viz také

[Platform::Collections – obor názvů](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)