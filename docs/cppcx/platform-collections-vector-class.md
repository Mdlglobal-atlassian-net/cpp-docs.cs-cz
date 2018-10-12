---
title: 'Platform::Collections:: Vector – třída | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acf3ae2fd16eb3aacbc0a2e681ae39aece1b4dd4
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163215"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections:: Vector – třída

Představuje kolekci sekvenční objektů, které mohou být přístupné samostatně podle indexu.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementů obsažených v objektu vektoru.

*E*<br/>
Určuje binární predikát pro testování rovnosti s hodnotami typu *T*. Výchozí hodnota je `std::equal_to<T>`.

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

1. celá čísla

1. Třída rozhraní ^

1. Třída Public ref class ^

1. Hodnota – struktura

1. Veřejný výčet tříd

**Vektoru** třída je konkrétní implementace jazyka C++ [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) rozhraní.

Pokud se pokusíte použít **vektoru** zadejte veřejné návratová hodnota nebo parametr, je vyvolána C3986 Chyba kompilátoru. Můžete chybu opravit změnou parametr nebo návratový typ hodnoty na [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Vector::Vector](#ctor)|Inicializuje novou instanci třídy vektoru.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vector::append](#append)|Vloží zadanou položku za poslední položky v aktuálním vektoru.|
|[Vector::clear](#clear)|Odstraní všechny elementy v aktuálním vektoru.|
|[Vector::First](#first)|Vrátí iterátor, který určuje první prvek ve vektoru.|
|[Vector::GetAt](#getat)|Načte prvek aktuální vektor, který se je identifikovat podle zadaného indexu.|
|[Vector::GetMany](#getmany)|Načte posloupnost položek z aktuální vektoru, počínaje zadaným indexem.|
|[Vector::GetView](#getview)|Vrátí zobrazení jen pro čtení vektoru; To znamená [Platform::Collections:: vectorview –](../cppcx/platform-collections-vectorview-class.md).|
|[Vector::IndexOf](#indexof)|Vyhledá zadanou položku v aktuální vektoru a pokud najde, vrátí index položky.|
|[Vector::InsertAt](#insertat)|Vloží zadanou položku do aktuálního vektoru za prvkem identifikovaný zadaného indexu.|
|[Vector::ReplaceAll](#replaceall)|Odstraní prvky v aktuální vektoru a pak vloží prvky ze zadaného pole.|
|[Vector::removeAt](#removeat)|Odstraní prvek identifikovaný zadaný index aktuální vektoru.|
|[Vector::RemoveAtEnd](#removeatend)|Odstraní prvek na konec aktuální vektoru.|
|[Vector::SetAt](#setat)|Zadaná hodnota přiřadí element v aktuálním vektoru, který je identifikován podle zadaného indexu.|
|[Vector::size](#size)|Vrátí počet prvků v aktuálním objektu vektoru.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|událost [Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Nastane při změně vektoru.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Vector`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="append"></a>  Vector::append – metoda

Vloží zadanou položku za poslední položky v aktuálním vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Položka ke vložení do vektoru. Typ *položky* je definován *T* typename.

## <a name="clear"></a>  Vector::clear – metoda

Odstraní všechny elementy v aktuálním vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Vector::First – metoda

Vrátí iterátor odkazující na první prvek ve vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor odkazující na první prvek ve vektoru.

### <a name="remarks"></a>Poznámky

Praktický způsob uložení iterátorů vrácené First() je přiřadit návratovou hodnotu proměnné, která je deklarována s **automaticky** klíčovým slovem odvození typu. Například `auto x = myVector->First();`. Tato iterátoru ví délka kolekce.

Když budete potřebovat pár iterátorů předání do funkce STL, používat bezplatné funkce [Windows::Foundation:: Collections –:: začít](../cppcx/begin-function.md) a [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="getat"></a>  Vector::GetAt – metoda

Načte prvek aktuální vektor, který se je identifikovat podle zadaného indexu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Nulovým základem celé číslo bez znaménka, která určuje konkrétní prvek v objektu vektoru.

### <a name="return-value"></a>Návratová hodnota

Element určené *index* parametru. Typ prvku je definován *T* typename.

## <a name="getmany"></a>  Vector::GetMany – metoda

Načte posloupnost položek z aktuální vektoru, počínaje zadaným indexem a zkopíruje je do pole přidělené volajícímu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parametry

*startIndex*<br/>
Index založený na nule začátek položky, které chcete načíst.

*cíl*<br/>
Pole přidělené volajícímu položek, které začíná v elementu určené *startIndex* a konec na poslední prvek ve vektoru.

### <a name="return-value"></a>Návratová hodnota

Počet položek načtených.

### <a name="remarks"></a>Poznámky

Tato funkce není určena pro použití přímo kódem na straně klienta. Používá se interně v [to_vector – funkce](../cppcx/to-vector-function.md) umožňující efektivní převodu instance Platform::Vector std::vector instancí.

## <a name="getview"></a>  Vector::GetView – metoda

Vrátí zobrazení jen pro čtení vektoru; To znamená, IVectorView.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Návratová hodnota

Objekt IVectorView.

## <a name="indexof"></a>  Vector::IndexOf – metoda

Vyhledá zadanou položku v aktuální vektoru a pokud najde, vrátí index položky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Položka k vyhledání.

*index*<br/>
Z nuly vycházející index položky-li parametr *hodnotu* je nalezen, jinak 0.

*Index* parametru je 0, pokud je první prvek vektoru položka nebo položka nebyla nalezena. Pokud je návratová hodnota **true**, položka byla nalezena a je první prvek; v opačném případě položka nebyla nalezena.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zadaná položka je jinak **false**.

### <a name="remarks"></a>Poznámky

IndexOf std::find_if používá k vyhledání položky. Typy vlastních prvků by proto přetížit operátory == a! = – operátor Chcete-li povolit rovnost vyžaduje tento find_if porovnání.

##  <a name="insertat"></a>  Vector::InsertAt – metoda

Vloží zadanou položku do aktuálního vektoru za prvkem identifikovaný zadaného indexu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parametry

*index*<br/>
Nulovým základem celé číslo bez znaménka, která určuje konkrétní prvek v objektu vektoru.

*Položka*<br/>
Položky k vložení do vektoru za prvek určeného *index*. Typ *položky* je definován *T* typename.

## <a name="removeat"></a>  Vector::removeAt – metoda

Odstraní prvek identifikovaný zadaný index aktuální vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Nulovým základem celé číslo bez znaménka, která určuje konkrétní prvek v objektu vektoru.

## <a name="removeatend"></a>  Vector::RemoveAtEnd – metoda

Odstraní prvek na konec aktuální vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>  Vector::ReplaceAll – metoda

Odstraní prvky v aktuální vektoru a pak vloží prvky ze zadaného pole.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parametry

*směrování žádostí na aplikace*<br/>
Pole objektů, jehož typ je definován *T* typename.

## <a name="setat"></a>  Vector::SetAt – metoda

Zadaná hodnota přiřadí element v aktuálním vektoru, který je identifikován podle zadaného indexu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Nulovým základem celé číslo bez znaménka, která určuje konkrétní prvek v objektu vektoru.

*Položka*<br/>
Hodnota pro přiřazení k zadanému prvku. Typ *položky* je definován *T* typename.

## <a name="size"></a>  Vector::size – metoda

Vrátí počet prvků v aktuálním objektu vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků ve vektoru aktuální.

## <a name="ctor"></a>  Vector::Vector konstruktor

Inicializuje novou instanci třídy vektoru.

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
A [std::array](../standard-library/array-class-stl.md) , který se použije k inicializují vektor.

*směrování žádostí na aplikace*<br/>
A [Platform::Array](../cppcx/platform-array-class.md) , který se použije k inicializují vektor.

*Inicializace*<br/>
Typ kolekce objektů, které slouží k inicializaci aktuální vektoru.

*IL*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md) objektů typu *T* , který se použije k inicializují vektor.

*N*<br/>
Počet prvků v kolekci objektů, které slouží k inicializaci aktuální vektoru.

*Velikost*<br/>
Počet prvků ve vektoru.

*value*<br/>
Hodnota, která slouží k inicializaci každý prvek v aktuální vektoru.

*v*<br/>
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::vector](../standard-library/vector-class.md) , který slouží k inicializaci aktuální vektoru.

*ptr*<br/>
Ukazatel `std::vector` , který slouží k inicializaci aktuální vektoru.

*první*<br/>
První prvek v sekvenci objektů, které se používají k inicializaci aktuální vektoru. Typ *první* je předáno *perfektní přesměrování*. Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

*poslední*<br/>
Po posledním prvku v sekvenci objektů, které se používají k inicializaci aktuální vektoru. Typ *poslední* je předáno *perfektní přesměrování*. Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také

[Platforma Namespace](platform-namespace-c-cx.md)<br/>
[Vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)