---
title: Platform::Collections::VectorView – třída
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
ms.openlocfilehash: cecbd61ad8862d5046cab9e0b418d5c4d16829d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363809"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView – třída

Představuje zobrazení jen pro čtení sekvenční kolekce objektů, které lze jednotlivě přistupovat index. Typ každého objektu v kolekci je určen parametrem šablony.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ prvků obsažených v `VectorView` objektu.

*E*<br/>
Určuje binární predikát pro testování rovnosti `T`s hodnotami typu . Výchozí hodnota je `std::equal_to<T>`.

### <a name="remarks"></a>Poznámky

Třída `VectorView` implementuje [rozhraní Windows::Foundation::Collections::IVectorView\<T>](/uwp/api/Windows.Foundation.Collections.IVectorView_T_) rozhraní a podporu pro iterátory knihovny standardníšablony.

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Vektorové zobrazení::Vektorové zobrazení](#ctor)|Inicializuje novou instanci třídy VectorView.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[VectorView::První](#first)|Vrátí iterátor, který určuje první prvek v VectorView.|
|[Vektorové zobrazení::Getat](#getat)|Načte prvek aktuální VectorView, který je označen zadaným indexem.|
|[VectorView::GetMany](#getmany)|Načte posloupnost položek z aktuálního VectorView, počínaje zadaným indexem.|
|[Vektorové zobrazení::indexof](#indexof)|Vyhledá zadanou položku v aktuálním VectorView a pokud je nalezena, vrátí index položky.|
|[Vektorové zobrazení::Velikost](#size)|Vrátí počet prvků v aktuálním objektu VectorView.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VectorView`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView::První metoda

Vrátí iterátor, který určuje první prvek v VectorView.

### <a name="syntax"></a>Syntaxe

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek v VectorView.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak podržet iterátor vrácený First() je přiřadit vrácenou hodnotu proměnné, která je deklarována s klíčovým slovem **automatického** odpočtu typu. Například, `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView::Getatova metoda

Načte prvek aktuální VectorView, který je označen zadaným indexem.

### <a name="syntax"></a>Syntaxe

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Celé číslo bez znaménka s nulovým základem, které určuje určitý prvek v objektu VectorView.

### <a name="return-value"></a>Návratová hodnota

Prvek určený parametrem. `index` Typ prvku je určen parametrem šablony VectorView *T*.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView::Metoda GetMany

Načte posloupnost položek z aktuálního VectorView, počínaje zadaným indexem.

### <a name="syntax"></a>Syntaxe

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Parametry

*Startindex*<br/>
Nula na základě indexu začátku položky načíst.

*Dest*<br/>
Po dokončení této operace pole položek, které začínají `startIndex` na prvek určený a konec na poslední prvek v VectorView.

### <a name="return-value"></a>Návratová hodnota

Počet načtených položek.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView::Metoda IndexOf

Vyhledá zadanou položku v aktuálním VectorView a pokud je nalezena, vrátí index položky.

### <a name="syntax"></a>Syntaxe

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Parametry

*Hodnotu*<br/>
Položka, kterou chcete najít.

*Index*<br/>
Index na základě nuly položky, pokud je nalezen parametr; `value` jinak 0.

Parametr *indexu* je 0, pokud je položka `VectorView` prvním prvkem položky nebo položka nebyla nalezena. Pokud je vrácená hodnota **true**, položka byla nalezena a je to první prvek; v opačném případě nebyla položka nalezena.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je nalezena zadaná položka; jinak **false**.

## <a name="vectorviewsize-method"></a><a name="size"></a>Vektorové zobrazení::Metoda velikosti

Vrátí počet prvků v aktuálním objektu VectorView.

### <a name="syntax"></a>Syntaxe

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v aktuálnívectorview.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>Vektorové zobrazení::Konstruktor VectorView

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

*Init*<br/>
Typ kolekce objektů, který se používá k inicializaci aktuální VectorView.

*Il*<br/>
[Std::initializer_list](../standard-library/initializer-list-class.md) jehož prvky budou použity k inicializaci VectorView.

*N*<br/>
Počet prvků v kolekci objektů, který se používá k inicializaci aktuální VectorView.

*Velikost*<br/>
Počet prvků v VectorView.

*Hodnotu*<br/>
Hodnota, která se používá k inicializaci každého prvku v aktuálním VectorView.

*V*<br/>
[Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) na [std::vector,](../standard-library/vector-class.md) který se používá k inicializaci aktuální VectorView.

*Ptr*<br/>
Ukazatel na `std::vector` který se používá k inicializaci aktuální VectorView.

*Arr*<br/>
A [Platform::Array](../cppcx/platform-array-class.md) objekt, který se používá k inicializaci aktuální VectorView.

*A*<br/>
[Std::array](../standard-library/array-class-stl.md) objekt, který se používá k inicializaci aktuální VectorView.

*První*<br/>
První prvek v posloupnosti objektů, které se používají k inicializaci aktuální VectorView. Typ je `first` předán pomocí *dokonalého předávání*. Další informace naleznete v tématu [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*Poslední*<br/>
Poslední prvek v posloupnosti objektů, které se používají k inicializaci aktuální VectorView. Typ je `last` předán pomocí *dokonalého předávání*. Další informace naleznete v tématu [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření součástí prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
