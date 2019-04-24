---
title: 'Platform::Collections:: vectorview – třída'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: 02b5e15a816ec057bfb0a8201b7591e628c3ea2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161378"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections:: vectorview – třída

Představuje sekvenční kolekce objektů, které mohou být přístupné samostatně podle indexu zobrazení jen pro čtení. Typ jednotlivých objektů v kolekci je určen parametrem šablony.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementů obsažených ve `VectorView` objektu.

*E*<br/>
Určuje binární predikát pro testování rovnosti s hodnotami typu `T`. Výchozí hodnota je `std::equal_to<T>`.

### <a name="remarks"></a>Poznámky

`VectorView` Implementuje třída [Windows::Foundation::Collections::IVectorView\<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_) rozhraní a podpora pro iterátorů standardní knihovny šablon.

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|Inicializuje novou instanci třídy VectorView.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[VectorView::First](#first)|Vrátí iterátor, který určuje první prvek v VectorView.|
|[VectorView::GetAt](#getat)|Načte prvek aktuální VectorView uvedený v zadaném indexu.|
|[VectorView::GetMany](#getmany)|Načte posloupnost položek z aktuální VectorView počínaje zadaným indexem.|
|[VectorView::IndexOf](#indexof)|Vyhledá zadanou položku v aktuální VectorView a pokud najde, vrátí index položky.|
|[VectorView::Size](#size)|Vrátí počet prvků v aktuálním objektu VectorView.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VectorView`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="first"></a>  VectorView::First – metoda

Vrátí iterátor, který určuje první prvek v VectorView.

### <a name="syntax"></a>Syntaxe

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v VectorView.

### <a name="remarks"></a>Poznámky

Praktický způsob uložení iterátorů vrácené First() je přiřadit návratovou hodnotu proměnné, která je deklarována s **automaticky** klíčovým slovem odvození typu. Například, `auto x = myVectorView->First();`.

## <a name="getat"></a>  VectorView::GetAt – metoda

Načte prvek aktuální VectorView uvedený v zadaném indexu.

### <a name="syntax"></a>Syntaxe

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Nulovým základem celé číslo bez znaménka, která určuje konkrétní prvek v objektu VectorView.

### <a name="return-value"></a>Návratová hodnota

Element určené `index` parametru. Typ prvku je určeno parametrem šablony VectorView, *T*.

## <a name="getmany"></a>  VectorView::GetMany – metoda

Načte posloupnost položek z aktuální VectorView počínaje zadaným indexem.

### <a name="syntax"></a>Syntaxe

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Parametry

*startIndex*<br/>
Index založený na nule začátek položky, které chcete načíst.

*dest*<br/>
Když tato operace dokončí, pole položek, které začíná v elementu určené `startIndex` a Konec po posledním prvku v VectorView.

### <a name="return-value"></a>Návratová hodnota

Počet položek načtených.

## <a name="indexof"></a>  VectorView::IndexOf – metoda

Vyhledá zadanou položku v aktuální VectorView a pokud najde, vrátí index položky.

### <a name="syntax"></a>Syntaxe

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Položka k vyhledání.

*index*<br/>
Z nuly vycházející index položky-li parametr `value` je nalezen, jinak 0.

*Index* parametru je 0, pokud je první prvek buď položka `VectorView` nebo položka nebyla nalezena. Pokud je návratová hodnota **true**, položka byla nalezena a je první prvek; v opačném případě položka nebyla nalezena.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zadaná položka je jinak **false**.

## <a name="size"></a>  VectorView::Size – metoda

Vrátí počet prvků v aktuálním objektu VectorView.

### <a name="syntax"></a>Syntaxe

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v aktuální VectorView.

## <a name="ctor"></a>  VectorView::VectorView konstruktor

Inicializuje novou instanci třídy VectorView.

### <a name="syntax"></a>Syntaxe

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>Parametry

*Inicializace*<br/>
Typ kolekce objektů, které slouží k inicializaci aktuální VectorView.

*il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) jehož prvky se použije k inicializaci VectorView.

*N*<br/>
Počet prvků v kolekci objektů, které slouží k inicializaci aktuální VectorView.

*Velikost*<br/>
Počet prvků v VectorView.

*value*<br/>
Hodnota, která slouží k inicializaci každý prvek v aktuální VectorView.

*v*<br/>
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::vector](../standard-library/vector-class.md) , který slouží k inicializaci aktuální VectorView.

*ptr*<br/>
Ukazatel `std::vector` , který slouží k inicializaci aktuální VectorView.

*arr*<br/>
A [Platform::Array](../cppcx/platform-array-class.md) objekt, který slouží k inicializaci aktuální VectorView.

*a*<br/>
A [std::array](../standard-library/array-class-stl.md) objekt, který slouží k inicializaci aktuální VectorView.

*první*<br/>
První prvek v sekvenci objektů, které se používají k inicializaci aktuální VectorView. Typ `first` je předáno *perfektní přesměrování*. Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Po posledním prvku v sekvenci objektů, které se používají k inicializaci aktuální VectorView. Typ `last` je předáno *perfektní přesměrování*. Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)<br/>
[Vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
