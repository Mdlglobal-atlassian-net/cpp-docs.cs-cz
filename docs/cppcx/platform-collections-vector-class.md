---
title: Platform::Collections::Vector – třída
ms.date: 12/04/2019
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
ms.openlocfilehash: 60c82a113bc19e9652af8c1ad531e1c479077f20
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032119"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector – třída

Představuje sekvenční kolekci objektů, které lze jednotlivě přistupovat index. Implementuje [Windows::Foundation::Collections::IObservableVector,](/uwp/api/windows.foundation.collections.iobservablevector-1) který pomáhá s [datovou vazbou](/windows/uwp/data-binding/data-binding-in-depth)XAML .

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ prvků obsažených v objektu Vector.

*E*<br/>
Určuje binární predikát pro testování rovnosti s hodnotami typu *T*. Výchozí hodnota `std::equal_to<T>`je .

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

1. celá čísla

1. třída rozhraní^

1. veřejné ref třídy^

1. hodnota struktura

1. třída veřejného výčtu

Vector **Vector** Třída je C++ konkrétní implementace [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1) rozhraní.

Pokud se pokusíte použít **typ Vector** ve veřejné vrácené hodnotě nebo parametru, je vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou parametru nebo typu vrácené hodnoty [systému Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1). Další informace naleznete v [tématu Kolekce (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Vektor::Vektor](#ctor)|Inicializuje novou instanci třídy Vector.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vektor::Připojit](#append)|Vloží zadanou položku za poslední položku v aktuální vektorové položce.|
|[Vektor::Vymazat](#clear)|Odstraní všechny prvky v aktuálním vektoru.|
|[Vektor::První](#first)|Vrátí iterátor, který určuje první prvek ve Vektoru.|
|[vektor::Getat](#getat)|Načte prvek aktuální ho vektoru, který je identifikován zadaným indexem.|
|[Vektor::GetMany](#getmany)|Načte posloupnost položek z aktuálního vektoru, počínaje zadaným indexem.|
|[Vektor::GetView](#getview)|Vrátí zobrazení vektoru jen pro čtení; to znamená [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[vektor::indexof](#indexof)|Vyhledá zadanou položku v aktuálním vektoru a pokud je nalezena, vrátí index položky.|
|[vektor:insertat](#insertat)|Vloží zadanou položku do aktuálního vektoru na prvek identifikovaný zadaným indexem.|
|[Vektor::ReplaceAll](#replaceall)|Odstraní prvky v aktuálním vektoru a potom vloží prvky ze zadaného pole.|
|[vektor::Removeat](#removeat)|Odstraní prvek identifikovaný zadaným indexem z aktuálního vektoru.|
|[vektor::RemoveAtend](#removeatend)|Odstraní prvek na konci aktuálního vektoru.|
|[vektor::Setat](#setat)|Přiřadí zadanou hodnotu elementu v aktuálním vectoru, který je identifikován zadaným indexem.|
|[Vektor::Velikost](#size)|Vrátí počet prvků v aktuálním objektu Vector.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|událost [Windows::Foundation::Collection::VectorChangedEventHandler\<T>^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1)|Vyvolá se při změně vektoru.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Vector`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Obor názvů:** Platforma::Kolekce

## <a name="vectorappend-method"></a><a name="append"></a>Vektor::Metoda připojení

Vloží zadanou položku za poslední položku v aktuální vektorové položce.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Položka, kterou chcete vložit do vektoru. Typ *položky* je definován typem *T.*

## <a name="vectorclear-method"></a><a name="clear"></a>Vektor::Vymazat metodu

Odstraní všechny prvky v aktuálním vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>Vektor::První metoda

Vrátí iterátor, který odkazuje na první prvek ve Vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na první prvek ve Vektoru.

### <a name="remarks"></a>Poznámky

Pohodlný způsob, jak podržet iterátor vrácený First() je přiřadit vrácenou hodnotu proměnné, která je deklarována s klíčovým slovem **automatického** odpočtu typu. Například, `auto x = myVector->First();`. Tento iterátor zná délku kolekce.

Pokud potřebujete dvojici iterátorů předat funkci STL, použijte volné funkce [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) a [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a>vektor::Getatova metoda

Načte prvek aktuální ho vektoru, který je identifikován zadaným indexem.

### <a name="syntax"></a>Syntaxe

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Celé číslo bez znaménka s nulovým základem, které určuje určitý prvek v objektu Vector.

### <a name="return-value"></a>Návratová hodnota

Prvek určený parametrem *indexu.* Typ prvku je definován typem *T.*

## <a name="vectorgetmany-method"></a><a name="getmany"></a>Vektor::GetMany Metoda

Načte posloupnost položek z aktuálního vector, počínaje zadaný mačká a zkopíruje je do pole přidělené volajícím.

### <a name="syntax"></a>Syntaxe

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parametry

*Startindex*<br/>
Nula na základě indexu začátku položky načíst.

*Dest*<br/>
Volající přidělené pole položek, které začínají na prvek určený *startIndex* a konec na poslední prvek v Vector.

### <a name="return-value"></a>Návratová hodnota

Počet načtených položek.

### <a name="remarks"></a>Poznámky

Tato funkce není určena pro použití přímo klientským kódem. Interně se používá v [to_vector funkci,](../cppcx/to-vector-function.md) která umožňuje efektivní převod platformy::Vector intances na std::vector instance.

## <a name="vectorgetview-method"></a><a name="getview"></a>Vektor::Metoda GetView

Vrátí zobrazení vektoru jen pro čtení; to znamená IVectorView.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

Objekt IVectorView.

## <a name="vectorindexof-method"></a><a name="indexof"></a>vektor::metoda IndexOf

Vyhledá zadanou položku v aktuálním vektoru a pokud je nalezena, vrátí index položky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Položka, kterou chcete najít.

*Index*<br/>
Index na základě nuly položky, pokud je *nalezena hodnota parametru;* jinak 0.

Parametr *indexu* je 0, pokud je položka prvním prvkem vectoru nebo položka nebyla nalezena. Pokud je vrácená hodnota **true**, položka byla nalezena a je to první prvek; v opačném případě nebyla položka nalezena.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je nalezena zadaná položka; jinak **false**.

### <a name="remarks"></a>Poznámky

IndexOf používá std::find_if k vyhledání položky. Vlastní typy prvků by proto měly přetížit operátor == a !=, aby bylo možné povolit porovnání rovnosti, které find_if vyžaduje.

## <a name="vectorinsertat-method"></a><a name="insertat"></a>vektor::metoda insertat

Vloží zadanou položku do aktuálního vektoru na prvek identifikovaný zadaným indexem.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Celé číslo bez znaménka s nulovým základem, které určuje určitý prvek v objektu Vector.

*Položky*<br/>
Položka vložit do Vector na prvek určený *index*. Typ *položky* je definován typem *T.*

## <a name="vectorremoveat-method"></a><a name="removeat"></a>vektor::Metoda RemoveAt

Odstraní prvek identifikovaný zadaným indexem z aktuálního vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Celé číslo bez znaménka s nulovým základem, které určuje určitý prvek v objektu Vector.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>vektor::metoda Removeatend

Odstraní prvek na konci aktuálního vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>Vektor::Metoda ReplaceAll

Odstraní prvky v aktuálním vektoru a potom vloží prvky ze zadaného pole.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parametry

*Arr*<br/>
Pole objektů, jejichž typ je definován typem *T.*

## <a name="vectorsetat-method"></a><a name="setat"></a>vektor::Setatova metoda

Přiřadí zadanou hodnotu elementu v aktuálním vectoru, který je identifikován zadaným indexem.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Celé číslo bez znaménka s nulovým základem, které určuje určitý prvek v objektu Vector.

*Položky*<br/>
Hodnota přiřadit k zadanému prvku. Typ *položky* je definován typem *T.*

## <a name="vectorsize-method"></a><a name="size"></a>Vektor::Metoda velikosti

Vrátí počet prvků v aktuálním objektu Vector.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v aktuálním Vector.

## <a name="vectorvector-constructor"></a><a name="ctor"></a>Vektor::Vektorový konstruktor

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

*A*<br/>
[Std::array,](../standard-library/array-class-stl.md) které bude použito k inicializaci Vector.

*Arr*<br/>
[Platforma::Array,](../cppcx/platform-array-class.md) která bude použita k inicializaci Vector.

*Init*<br/>
Typ kolekce objektů, který se používá k inicializaci aktuální Vector.

*Il*<br/>
[Std::initializer_list](../standard-library/initializer-list-class.md) objektů typu *T,* které budou použity k inicializaci Vektoru.

*N*<br/>
Počet prvků v kolekci objektů, který se používá k inicializaci aktuální Vector.

*Velikost*<br/>
Počet prvků ve Vektoru.

*value*<br/>
Hodnota, která se používá k inicializaci každého prvku v aktuálním Vector.

*V*<br/>
[Lvalues a Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) na [std::vector,](../standard-library/vector-class.md) který se používá k inicializaci aktuální Vector.

*Ptr*<br/>
Ukazatel na `std::vector` který se používá k inicializaci aktuální Vector.

*První*<br/>
První prvek v posloupnosti objektů, které se používají k inicializaci aktuálního Vector. Typ *prvního* je předán pomocí *dokonalého předávání*. Další informace naleznete v tématu [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*Poslední*<br/>
Poslední prvek v sekvenci objektů, které se používají k inicializaci aktuální vector. Typ *posledního* je předán pomocí *dokonalého předávání*. Další informace naleznete v tématu [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také

[Kolekce (C++/CX)](collections-c-cx.md)<br/>
[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření součástí prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
