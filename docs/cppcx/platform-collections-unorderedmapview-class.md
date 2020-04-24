---
title: Platform::Collections::UnorderedMapView – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: f0096982ad5d11b9ea394c9f02ba748a52e4216b
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031482"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView – třída

Představuje zobrazení jen pro čtení do *mapy*, což je kolekce párů klíč hodnota.

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
Typ, který poskytuje objekt funkce, který může porovnat dvě klíčové hodnoty rovnosti. Ve výchozím nastavení [\<std::equal_to K>](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Poznámky

UnorderedMapView je konkrétní implementace [C++ systému Windows::Foundation::Collections::IMapView\<K,V>](/uwp/api/windows.foundation.collections.imapview-2) rozhraní, které je předáváno přes binární rozhraní aplikace (ABI). Další informace naleznete v [tématu Kolekce (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|Inicializuje novou instanci unorderedMapView třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[UnorderedMapView::První](#first)|Vrátí iterátor, který je inicializován na první prvek v zobrazení mapy.|
|[UnorderedMapView::HasKey](#haskey)|Určuje, zda aktuální UnorderedMapView obsahuje zadaný klíč.|
|[UnorderedMapView::Vyhledávání](#lookup)|Načte prvek na zadaný klíč v aktuální unorderedMapView objektu.|
|[UnorderedMapView::Velikost](#size)|Vrátí počet prvků v aktuálním objektu UnorderedMapView.|
|[UnorderedMapView::Rozdělit](#split)|Rozdělí původní UnorderedMapView objekt do dvou UnorderedMapView objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`UnorderedMapView`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>UnorderedMapView::První metoda

Vrátí iterátor, který určuje první [prvek Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) prvek v neuspořádané mapě.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v zobrazení mapy.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak podržet iterátor vrácený First() je přiřadit vrácenou hodnotu proměnné, která je deklarována s klíčovým slovem **automatického** odpočtu typu. Například, `auto x = myMapView->First();`.

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>UnorderedMapView::Metoda HasKey

Určuje, zda aktuální UnorderedMap obsahuje zadaný klíč.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč použitý k vyhledání prvku. Typ `key` je typename *K*.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je nalezen klíč; jinak **false**.

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>UnorderedMapView::Metoda vyhledávání

Načte hodnotu typu V, která je přidružena k zadanému klíči typu K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč slouží k vyhledání prvku v UnorderedMapView. Typ `key` je typename *K*.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která je `key`spárována s . Typ vrácené hodnoty je typename *V*.

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>UnorderedMapView::Metoda velikosti

Vrátí počet [windows::foundation::collections::iKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) prvky v UnorderedMapView.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v Neuspořádané MapView.

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>UnorderedMapView::Metoda rozdělení

Rozdělí aktuální UnorderedMapView objekt do dvou UnorderedMapView objekty. Tato metoda není funkční.

### <a name="syntax"></a>Syntaxe

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>Parametry

*první oddíl*<br/>
První část původní hodu NeorderedMapView objektu.

*druhý oddíl*<br/>
Druhá část původní ho disponiál UnorderedMapView objektu.

### <a name="remarks"></a>Poznámky

Tato metoda není funkční; to nedělá nic.

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>UnorderedMapView::Neuspořádaný konstruktor Zobrazení mapy

Inicializuje novou instanci unorderedMapView třídy.

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

*N*<br/>
Počet prvků, pro které chcete předem přidělit místo.

*Init*<br/>
Název typu UnorderedMapView.

*H*<br/>
Objekt funkce, který může hodnotu hash pro klíč. Výchozí hodnota [std::hash\<K>](../standard-library/hash-class.md) pro typy, které `std::hash` podporuje.

*P*<br/>
Typ, který poskytuje objekt funkce, který může porovnat dva klíče k určení jejich rovnosti. Výchozí je [\<std::equal_to K>](../standard-library/equal-to-struct.md).

*M*<br/>
Odkaz nebo [Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) na [std::unordered_map,](../standard-library/unordered-map-class.md) který se používá k inicializaci UnorderedMapView.

*První*<br/>
Vstupní iterátor prvního prvku v rozsahu prvků použitých k inicializaci UnorderedMapView.

*Poslední*<br/>
Vstupní iterátor prvního prvku po rozsahu prvků použitých k inicializaci UnorderedMapView.

## <a name="see-also"></a>Viz také

[Platforma::Obor názvů kolekcí](../cppcx/platform-collections-namespace.md)<br/>
[Okna::Založení::IMapView](/uwp/api/windows.foundation.collections.imapview-2)
