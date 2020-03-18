---
title: Vector&lt;bool&gt; třídy
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
ms.openlocfilehash: 4043b46bf2f93b362de029577fe9ac3c11dbcaa2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443926"
---
# <a name="vectorltboolgt-class"></a>Vector&lt;bool&gt; třídy

Třída `vector<bool>` je Částečná specializace [vektoru](../standard-library/vector-class.md) pro prvky typu **bool**. Má Alokátor pro základní typ, který je použit specializací, která poskytuje optimalizaci místa uložením jedné **bool** hodnoty na bit.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Poznámky

Tato specializace šablony třídy se chová jako vektor, s výjimkou rozdílů, které jsou vysvětleny v tomto článku.

Operace, které se zabývat s typem **bool** , odpovídají hodnotám v kontejneru úložiště. pro sestavování těchto hodnot se `allocator_traits::construct` nepoužívá.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_pointer](#const_pointer)|Definice typu `const_iterator`, která může sloužit jako konstantní ukazatel na logický prvek `vector<bool>`.|
|[const_reference](#const_reference)|Typedef pro **bool**. Po inicializaci nekontroluje aktualizace původní hodnoty.|
|[ukazatele](#pointer)|Definice typu `iterator`, která může sloužit jako ukazatel na logický prvek `vector<bool>`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[funkci](#flip)|Obrátí všechny bity v `vector<bool>`.|
|[adresu](#swap)|Vyměňuje prvky dvou `vector<bool>`s.|
|[podnikatel&#91;&#93;](#op_at)|Vrátí simulovaný odkaz na prvek `vector<bool>` na zadané pozici.|
|`at`|Funguje stejně jako nespecializovaná funkce [Vector](../standard-library/vector-class.md):: at s tím rozdílem, že používá třídu proxy [vector\<bool >:: Reference](#reference_class). Viz také [operátor&#91;](#op_at).|
|`front`|Funguje stejně jako nespecializovaná funkce [Vector](../standard-library/vector-class.md):: front s tím rozdílem, že používá třídu proxy [vector\<bool >:: Reference](#reference_class). Viz také [operátor&#91;](#op_at).|
|`back`|Funguje stejně jako nespecializovaná funkce [Vector](../standard-library/vector-class.md):: back s tím rozdílem, že používá třídu proxy [vector\<bool >:: Reference](#reference_class). Viz také [operátor&#91;](#op_at).|

### <a name="proxy-class"></a>Třída proxy

|||
|-|-|
|[Vektorová třída\<bool > Reference](#reference_class)|Třída, která funguje jako proxy pro simulaci `bool&` chování a jejíž objekty mohou poskytnout odkazy na elementy (jednotlivé bity) v rámci objektu `vector<bool>`.|

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<Vector >

**Obor názvů:** std

## <a name="const_pointer"></a>Vector\<bool >:: const_pointer

Typ, který popisuje objekt, který může sloužit jako konstantní ukazatel na logický prvek sekvence obsažený objektem `vector<bool>`.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>Vector\<bool >:: const_reference

Typ, který popisuje objekt, který může sloužit jako konstantní odkaz na logický element sekvence obsažený objektem `vector<bool>`.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Poznámky

Další informace a příklady kódu naleznete v tématu [vector&lt;bool&gt;:: Reference:: operator =](#reference_operator_eq).

## <a name="flip"></a>Vector\<bool >:: flip

Obrátí všechny bity ve `vector<bool>`.

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

## <a name="op_at"></a>Vector\<bool >:: operator []

Vrátí simulovaný odkaz na prvek `vector<bool>` na zadané pozici.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*POS*|Pozice prvku `vector<bool>`.|

### <a name="return-value"></a>Návratová hodnota

[Vektor\<bool >:: Reference](#reference_class) nebo [vector\<bool >:: const_reference](#const_reference) objekt, který obsahuje hodnotu indexovaného elementu.

Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.

### <a name="remarks"></a>Poznámky

Pokud kompilujete pomocí _ITERATOR_DEBUG_LEVEL sady, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku mimo hranice vektoru.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

Tento příklad kódu ukazuje správné použití `vector<bool>::operator[]` a dvou běžných chyb kódování, které jsou zakomentovány. Tyto chyby způsobují chyby, protože nelze považovat adresu objektu `vector<bool>::reference`, který `vector<bool>::operator[]` vrací.

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

## <a name="pointer"></a>Vector\<bool >::p ointer

Typ, který popisuje objekt, který může sloužit jako ukazatel na logický prvek sekvence obsažený objektem `vector<bool>`.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>Vector\<bool >:: Reference – třída

Třída `vector<bool>::reference` je proxy třída poskytovaná pomocí [třídy vector\<bool >](../standard-library/vector-bool-class.md) pro simulaci `bool&`.

### <a name="remarks"></a>Poznámky

Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>` používá pouze jeden bit na prvek, na který lze odkazovat pomocí této třídy proxy. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například vzhledem k tomu, že adresa objektu `vector<bool>::reference` nelze vzít, následující kód, který používá [Vector\<bool >:: operator&#91; ](#op_at) není správný:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>Vector\<bool >:: Reference:: flip

Invertuje logickou hodnotu odkazovaného prvku [vector\<bool >](../standard-library/vector-bool-class.md) .

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

###  <a name="reference_operator_bool"></a>Vector\<bool >:: Reference:: operator bool

Poskytuje implicitní převod z `vector<bool>::reference` na **bool**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Návratová hodnota

Logická hodnota prvku objektu Vector\<bool >.

#### <a name="remarks"></a>Poznámky

Objekt `vector<bool>` nelze změnit pomocí tohoto operátoru.

###  <a name="reference_operator_eq"></a>Vector\<bool >:: Reference:: operator =

Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

*Pravé*\
Odkaz prvku, jehož hodnota má být přiřazena k bitu.

\ *Val*
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

## <a name="swap"></a>Vector\<bool >:: swap

Statická členská funkce, která vyměňuje dva prvky logických vektorů (`vector<bool>`) pomocí třídy proxy [vector\<bool >:: Reference](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

*Levý*\
Prvek, který má být vyměněn pomocí *pravého* prvku.

*Pravé*\
Prvek, který má být vyměněn pomocí *levého* prvku.

### <a name="remarks"></a>Poznámky

Toto přetížení podporuje speciální požadavky proxy serveru `vector<bool>`. [Vector](../standard-library/vector-class.md):: swap má stejné funkce jako přetížení jednoho argumentu `vector<bool>::swap()`.

## <a name="see-also"></a>Viz také

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
