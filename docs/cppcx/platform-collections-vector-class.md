---
title: "Třída Platform::Collections::Vector | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00bf369942289752f7043ce5070618260a90c7ff
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector – třída

Představuje kolekci sekvenční objektů, které může být index individuálně získávat přístup.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parametry

*T*  
Typ elementů obsažených v objektu vektoru.

*E*  
Určuje binární predikát pro testování rovnosti s hodnotami typu *T*. Výchozí hodnota je `std::equal_to<T>`.

### <a name="remarks"></a>Poznámky

Povolené typy jsou:

1. celá čísla

1. Třída rozhraní ^

1. Třída veřejné ref ^

1. Hodnota – struktura

1. Veřejný výčet tříd

**Vektoru** třída je konkrétní implementace C++ [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) rozhraní.

Pokud pokus o použití **vektoru** zadejte veřejný návratovou hodnotu nebo parametru, je vyvolána C3986 Chyba kompilátoru. Můžete opravte chybu tak, že změníte parametr nebo vrátí typ hodnoty k [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Vector::Vector](#ctor)|Inicializuje novou instanci třídy vektoru.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vector::append](#append)|Vloží zadanou položku za poslední položky v aktuální vektoru.|
|[Vector::clear](#clear)|Odstraní všechny elementy v aktuálním vektoru.|
|[Vector::First](#first)|Vrátí iterátor, který určuje první prvek v vektoru.|
|[Vector::GetAt](#getat)|Načte element aktuální vektor, který je identifikovat pomocí zadaného indexu.|
|[Vector::GetMany](#getmany)|Načte posloupnost položek z aktuální vektoru, počínaje zadaným indexem.|
|[Vector::GetView](#getview)|Vrátí vektor; zobrazení jen pro čtení To znamená [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vector::IndexOf](#indexof)|Vyhledá zadanou položku v aktuální vektoru a pokud najde, vrátí index položky.|
|[Vector::InsertAt](#insertat)|Vloží zadanou položku do aktuální vektoru za elementem identifikovanou pomocí zadaného indexu.|
|[Vector::ReplaceAll](#replaceall)|Odstraní elementy v aktuálním vektoru a vloží elementy ze zadaného pole.|
|[Vector::removeAt](#removeat)|Odstraní element identifikovanou pomocí zadaného indexu z aktuální vektoru.|
|[Vector::RemoveAtEnd](#removeatend)|Odstraní prvek na konec aktuální vektoru.|
|[Vector::SetAt](#setat)|Zadaná hodnota přiřadí element v aktuální vektor, který je identifikován pomocí zadaného indexu.|
|[Vector::size](#size)|Vrátí počet prvků v aktuálním objektu vektoru.|

### <a name="events"></a>Události

|||
|-|-|
|Název|Popis|
|událost [Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|Nastane při změně vektoru.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Vector`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections

## <a name="append"></a>  Vector::append – metoda

Vloží zadanou položku za poslední položky v aktuální vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parametry

*index*  
Položka ke vložení do vektoru. Typ *položky* je definována *T* typename.

## <a name="clear"></a>  Vector::clear – metoda

Odstraní všechny elementy v aktuálním vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Vector::First – metoda

Vrátí iterovat této body prvním elementem v vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Návratová hodnota

Iterator, která odkazuje na prvním elementem v vektoru.

### <a name="remarks"></a>Poznámky

Pohodlný způsob pro uložení iterator vrácený First() je přiřadit návratovou hodnotu proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myVector->First();`. Tato iterator zná délce kolekce.

Pokud budete potřebovat pár iterátory předat do funkce STL, používat bezplatné funkce [Windows::Foundation::Collections:: začít](../cppcx/begin-function.md) a [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="getat"></a>  Vector::GetAt – metoda

Načte element aktuální vektor, který je identifikovat pomocí zadaného indexu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*  
Počítaný od nuly, nepodepsané číslo, které určuje konkrétní prvek v objektu vektoru.

### <a name="return-value"></a>Návratová hodnota

Element určeného *index* parametr. Typ elementu je definován *T* typename.

## <a name="getmany"></a>  Vector::GetMany – metoda

Načte posloupnost položek z aktuální vektoru, počínaje zadaným indexem a zkopíruje je do pole přidělené volajícího.

### <a name="syntax"></a>Syntaxe

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parametry

*startIndex*  
Index založený na nule spouštění položky, které chcete načíst.

*Cíle*  
Volající přidělené řadu položky, které začínají na element určeného *počáteční index* a konec na posledním prvkem v vektoru.

### <a name="return-value"></a>Návratová hodnota

Počet položek, které načíst.

### <a name="remarks"></a>Poznámky

Tato funkce není určen pro použití přímo v kódu klienta. Používá se interně v [to_vector funkce](../cppcx/to-vector-function.md) umožňující efektivní převod Platform::Vector intances std::vector instance.

## <a name="getview"></a>  Vector::GetView – metoda

Vrátí vektor; zobrazení jen pro čtení To znamená, IVectorView.

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

*value*  
Položka k vyhledání.

*index*  
Index založený na nule položky Pokud parametr *hodnotu* , jinak hodnota je 0.

*Index* parametru je 0, pokud položka je první prvek vektoru nebo položka nebyla nalezena. Pokud je vrácenou hodnotou `true`, položka byla nalezena a je první prvek; jinak, položka nebyla nalezena.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud zadaná položka není nalezena; v opačném `false`.

### <a name="remarks"></a>Poznámky

IndexOf std::find_if používá k nalezení položky. Vlastní element typy by proto přetížení == a! = – operátor Chcete-li povolit rovnosti vyžaduje tento find_if – porovnání.

##  <a name="insertat"></a>  Vector::InsertAt – metoda

Vloží zadanou položku do aktuální vektoru za elementem identifikovanou pomocí zadaného indexu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parametry

*index*  
Počítaný od nuly, nepodepsané číslo, které určuje konkrétní prvek v objektu vektoru.

Položka  
Položku, kterou chcete vložit do vektoru za elementem určeného *index*. Typ *položky* je definována *T* typename.

## <a name="removeat"></a>  Vector::removeAt – metoda

Odstraní element identifikovanou pomocí zadaného indexu z aktuální vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parametry

*index*  
Počítaný od nuly, nepodepsané číslo, které určuje konkrétní prvek v objektu vektoru.

## <a name="removeatend"></a>  Vector::RemoveAtEnd – metoda

Odstraní prvek na konec aktuální vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>  Vector::ReplaceAll – metoda

Odstraní elementy v aktuálním vektoru a vloží elementy ze zadaného pole.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parametry

*arr*  
Pole objektů, jejichž typ je definován *T* typename.

## <a name="setat"></a>  Vector::SetAt – metoda

Zadaná hodnota přiřadí element v aktuální vektor, který je identifikován pomocí zadaného indexu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parametry

*index*  
Počítaný od nuly, nepodepsané číslo, které určuje konkrétní prvek v objektu vektoru.

Položka  
Hodnota pro přiřazení daného elementu. Typ *položky* je definována *T* typename.

## <a name="size"></a>  Vector::size – metoda

Vrátí počet prvků v aktuálním objektu vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Návratová hodnota

Počet elementů v aktuální vektoru.

## <a name="ctor"></a>  Vector::Vector – konstruktor

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

*a*  
A [std::array](../standard-library/array-class-stl.md) který se použije k chybě při inicializaci vektoru.

*arr*  
A [Platform::Array](../cppcx/platform-array-class.md) který se použije k chybě při inicializaci vektoru.

*Init –*  
Typ na kolekci objektů, který se používá k chybě při inicializaci aktuální vektoru.

*IL*  
A [std::initializer_list](../standard-library/initializer-list-class.md) objektů typu *T* který se použije k chybě při inicializaci vektoru.

*N*  
Počet elementů v kolekci objektů, které slouží k inicializaci aktuální vektoru.

*Velikost*  
Počet elementů v vektoru.

*value*  
Hodnota, která se používá k chybě při inicializaci každý prvek v aktuální vektoru.

*v*  
[Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::vector](../standard-library/vector-class.md) používané k chybě při inicializaci aktuální vektoru.

*ptr*  
Ukazatel na `std::vector` používané k chybě při inicializaci aktuální vektoru.

*první*  
První prvek v pořadí objektů, které se používají k inicializaci aktuální vektoru. Typ *první* předávána prostřednictvím *ideální předávání*. Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*  
Posledním prvkem v pořadí objektů, které se používají k inicializaci aktuální vektoru. Typ *poslední* předávána prostřednictvím *ideální předávání*. Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Viz také

[Namespace platformy](platform-namespace-c-cx.md)  
[Vytváření Windows Runtime komponent v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  