---
title: 'Platform:: Collections:: Vector – třída'
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: a70856be04a63cad1c700cb3cc52711dde410265
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816582"
---
# <a name="platformcollectionsvector-class"></a>Platform:: Collections:: Vector – třída

Představuje sekvenční kolekci objektů, které mohou být jednotlivě dostupné pomocí indexu. Implementuje [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) pro usnadnění [vazby dat](/windows/uwp/data-binding/data-binding-in-depth)XAML.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ prvků obsažených v objektu Vector.

*E*<br/>
Určuje binární predikát pro testování rovnosti s hodnotami typu *T*. Výchozí hodnota je `std::equal_to<T>`.

### <a name="remarks"></a>Poznámky

Povolené typy:

1. celá čísla

1. Třída rozhraní ^

1. Třída Public ref class ^

1. struktura hodnoty

1. Public enum – třída

Třída **Vector** je C++ konkrétní implementace rozhraní [Windows:: Foundation:: Collections:: IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) .

Pokud se pokusíte použít **vektorový** typ ve veřejné návratové hodnotě nebo parametru, je vyvolána chyba kompilátoru C3986. Chybu můžete opravit tak, že změníte parametr nebo návratový typ hodnoty na [Windows:: Foundation:: Collections:: IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Další informace najdete v tématu [kolekce (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Members

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Vector::Vector](#ctor)|Inicializuje novou instanci třídy Vector.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vector:: Append](#append)|Vloží zadanou položku za poslední položku v aktuálním vektoru.|
|[Vector:: Clear](#clear)|Odstraní všechny prvky v aktuálním vektoru.|
|[Vector:: First](#first)|Vrátí iterátor, který určuje první prvek ve vektoru.|
|[Vector:: GetAt](#getat)|Načte prvek aktuálního vektoru, který je identifed zadaným indexem.|
|[Vector:: getmany](#getmany)|Načte sekvenci položek z aktuálního vektoru počínaje zadaným indexem.|
|[Vector:: GetView](#getview)|Vrátí zobrazení vektoru jen pro čtení. To znamená, že [Platform:: Collections:: VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vector:: IndexOf](#indexof)|Vyhledá zadanou položku v aktuálním vektoru a pokud ji najde, vrátí index položky.|
|[Vector:: InsertAt](#insertat)|Vloží zadanou položku do aktuálního vektoru po elementu identifikovaném zadaným indexem.|
|[Vector:: nahradit všechno](#replaceall)|Odstraní prvky v aktuálním vektoru a poté vloží prvky ze zadaného pole.|
|[Vector:: funkce RemoveAt](#removeat)|Odstraní element identifikovaný zadaným indexem z aktuálního vektoru.|
|[Vector:: RemoveAtEnd](#removeatend)|Odstraní prvek na konci aktuálního vektoru.|
|[Vector:: SetAt](#setat)|Přiřadí zadanou hodnotu k elementu v aktuálním vektoru, který je identifikován zadaným indexem.|
|[Vector:: size](#size)|Vrátí počet prvků v aktuálním objektu Vector.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|[Windows události:: Foundation:: Collection:: VectorChangedEventHandler\<t > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Nastane, pokud se změní vektor.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Vector`

### <a name="requirements"></a>Požadavky

**Header:** Collection. h

**Obor názvů:** Platform:: Collections

## <a name="append"></a>Vector:: Append – metoda

Vloží zadanou položku za poslední položku v aktuálním vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Položka, která má být vložena do vektoru. Typ *položky* je definován pomocí typeName *T* .

## <a name="clear"></a>Vector:: Clear – metoda

Odstraní všechny prvky v aktuálním vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>Vector:: First – metoda

Vrátí iterátor, který odkazuje na první prvek ve vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na první prvek v objektu Vector.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak uchovávat iterátory vrácené funkcí First (), je přiřadit návratovou hodnotu proměnné, která je deklarována s klíčovým slovem srážky typu **auto** . Například, `auto x = myVector->First();`. Tento iterátor zná délku kolekce.

Pokud potřebujete pár iterátorů předat funkci STL, použijte bezplatné funkce [Windows:: Foundation:: Collections:: begin](../cppcx/begin-function.md) a [Windows:: Foundation:: Collections:: end](../cppcx/end-function.md)

## <a name="getat"></a>Vector:: GetAt – metoda

Načte prvek aktuálního vektoru, který je identifed zadaným indexem.

### <a name="syntax"></a>Syntaxe

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Unsigned integer založený na nule, který určuje konkrétní prvek v objektu Vector.

### <a name="return-value"></a>Návratová hodnota

Element určený parametrem *indexu* . Typ elementu je definován pomocí typeName *T* .

## <a name="getmany"></a>Vector:: getmany – metoda

Načte sekvenci položek z aktuálního vektoru počínaje zadaným indexem a zkopíruje je do pole přiděleného volajícímu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parametry

*startIndex*<br/>
Index založený na nule začátku položek, které se mají načíst.

*propojovací*<br/>
Pole přidělené volajícímu, které začíná na elementu určeném parametrem *startIndex* a končí posledním prvkem ve vektoru.

### <a name="return-value"></a>Návratová hodnota

Počet načtených položek

### <a name="remarks"></a>Poznámky

Tato funkce není určena pro použití přímo klientským kódem. Používá se interně ve [funkci to_vector](../cppcx/to-vector-function.md) k zajištění efektivního převodu Platform:: Vector instance na instance std:: vector.

## <a name="getview"></a>Vector:: GetView – metoda

Vrátí zobrazení vektoru jen pro čtení. To znamená, že IVectorView.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

Objekt IVectorView.

## <a name="indexof"></a>Vector:: IndexOf – metoda

Vyhledá zadanou položku v aktuálním vektoru a pokud ji najde, vrátí index položky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Položka, kterou chcete najít.

*index*<br/>
Index založený na nule položky, pokud je nalezena *hodnota* parametru; v opačném případě 0.

Parametr *index* je 0, pokud buď je položka prvním prvkem vektoru, nebo položka nebyla nalezena. Pokud je vrácená hodnota **true**, položka byla nalezena a jedná se o první prvek; v opačném případě položka nebyla nalezena.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se zadaná položka najde; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

IndexOf používá k vyhledání položky std:: find_if. Vlastní typy prvků by proto měly přetížit operátor = = a! =, aby bylo možné povolit porovnávání rovnosti, které find_if vyžaduje.

##  <a name="insertat"></a>Vector:: InsertAt – metoda

Vloží zadanou položku do aktuálního vektoru po elementu identifikovaném zadaným indexem.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parametry

*index*<br/>
Unsigned integer založený na nule, který určuje konkrétní prvek v objektu Vector.

*položkami*<br/>
Položka, která má být vložena do vektoru za prvkem specifikovaným *indexem*. Typ *položky* je definován pomocí typeName *T* .

## <a name="removeat"></a>Vector:: funkce RemoveAt – metoda

Odstraní element identifikovaný zadaným indexem z aktuálního vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Unsigned integer založený na nule, který určuje konkrétní prvek v objektu Vector.

## <a name="removeatend"></a>Vector:: RemoveAtEnd – metoda

Odstraní prvek na konci aktuálního vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>Vector:: nahradit všechno – metoda

Odstraní prvky v aktuálním vektoru a poté vloží prvky ze zadaného pole.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parametry

*šipka*<br/>
Pole objektů, jejichž typ je definován pomocí typeName *T* .

## <a name="setat"></a>Vector:: SetAt – metoda

Přiřadí zadanou hodnotu k elementu v aktuálním vektoru, který je identifikován zadaným indexem.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Unsigned integer založený na nule, který určuje konkrétní prvek v objektu Vector.

*položkami*<br/>
Hodnota, která má být přiřazena k určitému elementu. Typ *položky* je definován pomocí typeName *T* .

## <a name="size"></a>Vector:: size – metoda

Vrátí počet prvků v aktuálním objektu Vector.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v aktuálním vektoru.

## <a name="ctor"></a>Vector:: Vector – konstruktor

Inicializuje novou instanci třídy Vector.

### <a name="syntax"></a>Syntaxe

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>Parametry

*a*<br/>
[Std:: Array](../standard-library/array-class-stl.md) , který bude použit k inicializaci vektoru.

*šipka*<br/>
[Platform:: Array](../cppcx/platform-array-class.md) , který se použije k inicializaci vektoru.

*For*<br/>
Typ kolekce objektů, které se používají k inicializaci aktuálního vektoru.

*il*<br/>
[Std:: initializer_list](../standard-library/initializer-list-class.md) objektů typu *T* , které budou použity k inicializaci vektoru.

*N*<br/>
Počet prvků v kolekci objektů, které jsou použity k inicializaci aktuálního vektoru.

*hodnota*<br/>
Počet prvků ve vektoru.

*value*<br/>
Hodnota, která se používá k inicializaci každého prvku v aktuálním vektoru.

*v*<br/>
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) pro objekt [std:: Vector](../standard-library/vector-class.md) , který se používá k inicializaci aktuálního vektoru.

*ptr*<br/>
Ukazatel na `std::vector`, který se používá k inicializaci aktuálního vektoru.

*first*<br/>
První prvek v sekvenci objektů, které se používají k inicializaci aktuálního vektoru. Typ *prvního* je předán pomocí způsobu *dokonalého předávání*. Další informace naleznete v tématu [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

*posledního*<br/>
Poslední prvek v sekvenci objektů, které se používají k inicializaci aktuálního vektoru. Typ *Poslední* se předává pomocí *metody dokonalého přesměrování*. Další informace naleznete v tématu [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také:

[Kolekce (C++/CX)](collections-c-cx.md)<br/>
[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření komponent prostředí Windows Runtime v nástrojiC++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
