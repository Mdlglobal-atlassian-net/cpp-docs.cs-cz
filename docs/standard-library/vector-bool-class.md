---
title: třída&lt;vektorového bool&gt;
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::flip
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: 6c67e3d9ba1b33cb99a7d3afb2522f443003fa38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376083"
---
# <a name="vectorltboolgt-class"></a>třída&lt;vektorového bool&gt;

Třída `vector<bool>` je částečná specializace [vektoru](../standard-library/vector-class.md) pro prvky typu **bool**. Má alokátor pro základní typ, který se používá specializace, která poskytuje optimalizaci prostoru uložením jedné **bool** hodnoty na bit.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Poznámky

Tato specializace šablony třídy se chová jako vektor, s výjimkou rozdílů vysvětlených v tomto článku.

Operace, které se zabývají **bool** typu odpovídají hodnotám v kontejneru úložiště. `allocator_traits::construct`se nepoužívá k vytvoření těchto hodnot.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_pointer](#const_pointer)|Typedef na `const_iterator` který může sloužit jako konstantní ukazatel na `vector<bool>`logický prvek .|
|[const_reference](#const_reference)|Typedef pro **bool**. Po inicializaci nekontroluje aktualizace původní hodnoty.|
|[ukazatel](#pointer)|Typedef na `iterator` který může sloužit jako ukazatel na logický `vector<bool>`prvek .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Flip](#flip)|Obrátí všechny bity `vector<bool>`v .|
|[Swap](#swap)|Vyměňuje prvky `vector<bool>`dvou s.|
|[operátor&#91;&#93;](#op_at)|Vrátí simulovaný odkaz `vector<bool>` na prvek v zadané poloze.|
|`at`|Funguje stejně jako nespecializovaný [vektor](../standard-library/vector-class.md)::at funkce, s tím rozdílem, že používá třídu proxy [třídy\<bool>::reference](#reference_class). Viz také [operátor&#91;&#93;](#op_at).|
|`front`|Funguje stejně jako nespecializovaný [vektor](../standard-library/vector-class.md)::front funkce, s tím rozdílem, že používá třídu proxy [třídy\<bool>::reference](#reference_class). Viz také [operátor&#91;&#93;](#op_at).|
|`back`|Funguje stejně jako nespecializovaný [vektor](../standard-library/vector-class.md)::back funkce, s tím rozdílem, že používá třídu proxy [třídy\<bool>::reference](#reference_class). Viz také [operátor&#91;&#93;](#op_at).|

### <a name="proxy-class"></a>Třída proxy

|||
|-|-|
|[vektorbool\<> referenční třídy](#reference_class)|Třída, která funguje jako `bool&` proxy pro simulaci chování a jejíž objekty mohou `vector<bool>` poskytovat odkazy na prvky (jednotlivé bity) v rámci objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví** \<: vektorové>

**Obor názvů:** std

## <a name="vectorboolconst_pointer"></a><a name="const_pointer"></a>vektorový\<bool>::const_pointer

Typ, který popisuje objekt, který může sloužit jako konstantní ukazatel na logický `vector<bool>` prvek sekvence obsažené v objektu.

```cpp
typedef const_iterator const_pointer;
```

## <a name="vectorboolconst_reference"></a><a name="const_reference"></a>vektorový\<bool>::const_reference

Typ, který popisuje objekt, který může sloužit jako konstantní odkaz na logický `vector<bool>` prvek sekvence obsažené v objektu.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Poznámky

Další informace a příklady kódu naleznete [v tématu&lt;vector bool&gt;::reference::operator=](#reference_operator_eq).

## <a name="vectorboolflip"></a><a name="flip"></a>vektorbool\<>::překlopit

Obrátí všechny bity `vector<bool>`v .

```cpp
void flip();
```

### <a name="example"></a>Příklad

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="vectorbooloperator"></a><a name="op_at"></a>vektorbool\<>::operátor[]

Vrátí simulovaný odkaz `vector<bool>` na prvek v zadané poloze.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Pos*|Pozice `vector<bool>` prvku.|

### <a name="return-value"></a>Návratová hodnota

[Vektorový\<bool>::reference](#reference_class) nebo [vector\<bool>::const_reference](#const_reference) objekt, který obsahuje hodnotu indexovaného prvku.

Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.

### <a name="remarks"></a>Poznámky

Pokud kompilujete s _ITERATOR_DEBUG_LEVEL nastavena, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku mimo hranice vektoru.  Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

Tento příklad kódu ukazuje `vector<bool>::operator[]` správné použití a dvě běžné chyby kódování, které jsou zakomentovány. Tyto chyby způsobit chyby, protože adresu objektu, `vector<bool>::reference` který `vector<bool>::operator[]` vrátí nelze přijmout.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="vectorboolpointer"></a><a name="pointer"></a>vektorbool\<>::pointer

Typ, který popisuje objekt, který může sloužit jako ukazatel na logický prvek `vector<bool>` sekvence obsažené v objektu.

```cpp
typedef iterator pointer;
```

## <a name="vectorboolreference-class"></a><a name="reference_class"></a>vektorbool\<>::referenční třída

Třída `vector<bool>::reference` je třída proxy poskytovaná [vector\<bool> Class](../standard-library/vector-bool-class.md) pro simulaci `bool&`.

### <a name="remarks"></a>Poznámky

Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>`používá pouze jeden bit na prvek, na který lze odkazovat pomocí této třídy proxy. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například protože adresu objektu `vector<bool>::reference` nelze převzít, následující kód, který používá vector [\<bool>::operátor&#91;&#93;](#op_at) není správný:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="vectorboolreferenceflip"></a><a name="reference_flip"></a>vektor\<bool>::reference::flip

Invertuje logickou hodnotu odkazovaného [vektorového\<bool>](../standard-library/vector-bool-class.md) elementu.

```cpp
void flip();
```

#### <a name="example"></a>Příklad

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

### <a name="vectorboolreferenceoperator-bool"></a><a name="reference_operator_bool"></a>vektor\<bool>::reference::operátor bool

Poskytuje implicitní `vector<bool>::reference` převod z **bool**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Návratová hodnota

Logická hodnota prvku vektorového\<bool> objektu.

#### <a name="remarks"></a>Poznámky

Tento `vector<bool>` operátor nemůže objekt změnit.

### <a name="vectorboolreferenceoperator"></a><a name="reference_operator_eq"></a>vektor\<bool>::reference::operátor=

Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz prvku, jehož hodnota má být přiřazena k bitu.

*Val*\
Logická hodnota, která má být přiřazena k bitu.

#### <a name="example"></a>Příklad

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="vectorboolswap"></a><a name="swap"></a>vektor\<bool>::swap

Statická členská funkce, která vyměňuje `vector<bool>`dva prvky boolean vektorů ( ) pomocí třídy proxy [vector\<bool>::reference](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Prvek, který má být vyměněn s *Right* element.

*Právo*\
Prvek, který má být vyměněn s *Left* element.

### <a name="remarks"></a>Poznámky

Toto přetížení podporuje speciální `vector<bool>`požadavky na proxy aplikace . [vector](../standard-library/vector-class.md)::swap má stejnou funkci jako přetížení `vector<bool>::swap()`jednoho argumentu .

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
