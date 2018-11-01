---
title: vektor&lt;bool&gt; třídy
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: 79b2231882f65715f47c774119c0e6e0608f1676
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455481"
---
# <a name="vectorltboolgt-class"></a>vektor&lt;bool&gt; třídy

`vector<bool>` Třída je částečná specializace [vektoru](../standard-library/vector-class.md) pro prvky typu **bool**. Má Alokátor pro základní typ, který je používán specializací a zajišťuje optimalizaci prostoru ukládáním **bool** hodnotu na bit.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Poznámky

Tato specializace šablony třídy se chová jako vektor, s výjimkou rozdílů popsaných v tomto článku.

Operace, které se zabývají **bool** typu odpovídají hodnotám v kontejneru úložiště. `allocator_traits::construct` se nepoužívá k vytváření těchto hodnot.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_pointer](#const_pointer)|Typedef pro `const_iterator` , který může sloužit jako konstantní ukazatel na prvek logické hodnoty `vector<bool>`.|
|[const_reference](#const_reference)|Definice typu **bool**. Po inicializaci nekontroluje aktualizace původní hodnoty.|
|[Ukazatel](#pointer)|Typedef pro `iterator` , který může sloužit jako ukazatel na prvek logické hodnoty `vector<bool>`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Převrátit na ose](#flip)|Obrátí všechny bity v `vector<bool>`.|
|[Prohození](#swap)|Vymění prvky dvou `vector<bool>`s.|
|[– operátor&#91;&#93;](#op_at)|Vrátí simulovaný odkaz `vector<bool>` prvek na zadané pozici.|
|`at`|Funguje stejně jako nespecializovaná [vektoru](../standard-library/vector-class.md):: ve funkci, s tím rozdílem, že používá třídu proxy [vektoru\<bool >:: reference](#reference_class). Viz také [operátor&#91;&#93;](#op_at).|
|`front`|Funguje stejně jako nespecializovaná [vektoru](../standard-library/vector-class.md):: přední funkce, s tím rozdílem, že používá třídu proxy [vektoru\<bool >:: reference](#reference_class). Viz také [operátor&#91;&#93;](#op_at).|
|`back`|Funguje stejně jako nespecializovaná [vektoru](../standard-library/vector-class.md):: zpět funkce, s tím rozdílem, že používá třídu proxy [vektoru\<bool >:: reference](#reference_class). Viz také [operátor&#91;&#93;](#op_at).|

### <a name="proxy-class"></a>Třída proxy

|||
|-|-|
|[vektor\<bool > reference – třída](#reference_class)|Třída, která funguje jako proxy pro simulaci `bool&` chování a jejíž objekty mohou poskytnout odkazy na prvky (jeden bit) v rámci `vector<bool>` objektu.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<vektoru >

**Namespace:** std

## <a name="const_pointer"></a>  vektor\<bool >:: const_pointer

Typ, který popisuje objekt, který může sloužit jako konstantní ukazatel na prvek logické hodnoty sekvence obsažený objektem `vector<bool>` objektu.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>  vektor\<bool >:: const_reference

Typ, který popisuje objekt, který může sloužit jako konstantní odkaz na prvek logické hodnoty sekvence obsažený objektem `vector<bool>` objektu.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Poznámky

Další informace a příklady kódu naleznete v tématu [vektoru&lt;bool&gt;:: reference::operator =](#reference_operator_eq).

## <a name="flip"></a>  vektor\<bool >:: flip

Obrátí všechny bity v `vector<bool>`.

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

## <a name="op_at"></a>  vektor\<bool >:: operator [].

Vrátí simulovaný odkaz `vector<bool>` prvek na zadané pozici.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*POS*|Pozice `vector<bool>` elementu.|

### <a name="return-value"></a>Návratová hodnota

A [vektoru\<bool >:: reference](#reference_class) nebo [vektoru\<bool >:: const_reference](#const_reference) objekt, který obsahuje hodnotu indexovaného prvku.

Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.

### <a name="remarks"></a>Poznámky

Pokud kompilujete s nastavenou _ITERATOR_DEBUG_LEVEL, nastane chyba za běhu při pokusu o přístup k prvku mimo hranice vektoru.  Další informace najdete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

Tento příklad kódu ukazuje správné použití `vector<bool>::operator[]` a dvě časté chyby kódování, které jsou okomentovány. Protože tyto chyby způsobují další chyby adresu `vector<bool>::reference` objekt, který `vector<bool>::operator[]` vrátí nelze provést.

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

## <a name="pointer"></a>  vektor\<bool >:: ukazatele

Typ, který popisuje objekt, který může sloužit jako ukazatel na prvek logické hodnoty sekvence obsažený objektem `vector<bool>` objektu.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>  vektor\<bool >:: reference – třída

`vector<bool>::reference` Třídy je třída proxy poskytnutá [vektoru\<bool > třída](../standard-library/vector-bool-class.md) pro simulaci `bool&`.

### <a name="remarks"></a>Poznámky

Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>` používá pouze jeden bit na element, který můžete odkazovat pomocí této třídy proxy serveru. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například protože adresu `vector<bool>::reference` nelze přijmout, následující kód, který používá [vektoru\<bool >:: – operátor&#91; &#93; ](#op_at) není správná:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>  vektor\<bool >:: reference::flip

Přemění logickou hodnotu odkazovaného [vektoru\<bool >](../standard-library/vector-bool-class.md) elementu.

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

###  <a name="reference_operator_bool"></a>  vektor\<bool >:: reference::operator bool

Poskytuje implicitní převod z `vector<bool>::reference` k **bool**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Návratová hodnota

Logická hodnota prvku vektoru\<bool > objektu.

#### <a name="remarks"></a>Poznámky

`vector<bool>` Objektu nelze změnit tímto operátorem.

###  <a name="reference_operator_eq"></a>  vektor\<bool >:: reference::operator =

Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz prvku, jehož hodnota má být přiřazena k bitu.

*Val*<br/>
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

## <a name="swap"></a>  vektor\<bool >:: swap

Statická členská funkce, která vyměňuje dva prvky vektorů logické hodnoty ( `vector<bool>`) pomocí serveru proxy třídy [vektoru\<bool >:: reference](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Element, který bude vyměněn za *vpravo* elementu.

*doprava*<br/>
Element, který bude vyměněn za *vlevo* elementu.

### <a name="remarks"></a>Poznámky

Toto přetížení podporuje zvláštní proxy požadavky `vector<bool>`. [vektor](../standard-library/vector-class.md):: swap má stejné funkce jako přetížení jedním argumentem `vector<bool>::swap()`.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
