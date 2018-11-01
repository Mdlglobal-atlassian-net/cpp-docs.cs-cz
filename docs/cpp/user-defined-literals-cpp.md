---
title: Uživateli definované literály (C++)
ms.date: 11/04/2016
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: 1de94b43423bb5b420be29d3cace146e265a1459
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665111"
---
# <a name="user-defined-literals--c"></a>Uživateli definované literály (C++)

Existuje pět hlavních kategorií literálů: celé číslo, znak, s plovoucí desetinnou čárkou, řetězec, logická hodnota a ukazatele.  Počínaje C++ 11, můžete definovat vlastní literálů na základě těchto kategorií k poskytování syntaktické klávesové zkratky pro společné idiomy a zvýšení typové bezpečnosti. Řekněme například, že máte třídu vzdálenost. Můžete definovat literál pro kilometrů a jinou pro mil a podporovat uživatele k explicitnímu měrné jednotky jednoduše napsáním: automatické d = 42.0_km nebo automaticky d = 42.0_mi. Neexistuje žádné výhody výkonu nebo nevýhodou uživateli definované literály jsou především ke zvýšení pohodlí nebo pro odvození typu v době kompilace. Standardní knihovna obsahuje uživateli definované literály std:string, std::complex a jednotky v čase a dobu trvání operace v \<chrono > hlavičky:

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
    std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
    complex<double> num =
        (2.0 + 3.01i) * (5.0 + 4.3i);       // Standard Library <complex> UDL
    auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Podpisy uživatelem definovaný operátor literálu

Implementovat uživatelem definovaného literálu definováním **operátor ""** v oboru názvů s jedním z následujících forem:

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const     char*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const  wchar_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Operátor názvy v předchozím příkladu jsou zástupné symboly pro jakýkoli název můžete zadat; vedoucí znaku podtržítka ale povinné. (Standardní knihovna může definovat literály bez podtržítko.) Návratový typ je, kde si přizpůsobit převod nebo jiné operace, která provádí literál. Kromě toho některé z těchto operátorů lze definovat jako `constexpr`.

## <a name="cooked-literals"></a>Vařené literály

Ve zdroji kód jakékoli literál, zda uživatelem nebo Ne, jako je v podstatě posloupnost alfanumerické znaky, `101`, nebo `54.7`, nebo `"hello"` nebo `true`. Kompilátor interpretuje pořadí jako celé číslo, float const char\* řetězec a tak dále. Uživatelem definovaného literálu, který přijímá jako vstup zadejte cokoli, co kompilátor přiřazená hodnota literálu je spor neformálně označované jako *vařené literál*. Všechny operátory výše, s výjimkou `_r` a `_t` jsou vařená literály. Například literál `42.0_km` by svázat operátor s názvem _km, který měl podobné _b a literál podpis `42_km` by svázat operátor podobný _a podpisem.

Následující příklad ukazuje, jak uživateli definované literály vstupní kontroly mohou pobídnout volající k explicitnímu svůj vstup. K vytvoření `Distance`, musí uživatel explicitně zadat kilometrech nebo mil pomocí vhodné uživatelem definovaného literálu. Samozřejmě můžete také dosažení stejného výsledku jiným způsobem, ale uživateli definované literály jsou míň podrobné než alternativ.

```cpp
struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double  val);
    friend Distance operator"" _mi(long double val);
    long double kilometers{ 0 };
public:
    long double get_kilometers() { return kilometers; }
    Distance operator+(Distance& other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

Distance operator"" _km(long double  val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * 1.6);
}
int main(int argc, char* argv[])
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    cout << "Kilometers in d: " << d.get_kilometers() << endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    cout << "Kilometers in d2: " << d2.get_kilometers() << endl;  //643.2

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    cout << "d3 value = " << d3.get_kilometers() << endl; // 99.6

    // Distance d4(90.0); // error constructor not accessible

    string s;
    getline(cin, s);
    return 0;
}
```

Všimněte si, že číslo literál musí používat desetinné číslo, jinak je číslo interpretován jako celé číslo a typ nemusí být kompatibilní s operátorem. Všimněte si také, že pro plovoucí desetinná čárka vstup, musí být typu **long double**a pro integrální typy musí být **long long**.

## <a name="raw-literals"></a>Literály nezpracovaných

V nezpracované uživatelem definovaného literálu operátor, který definujete přijímá literálu jako sekvenci hodnot typu char a je na vás k interpretaci tohoto pořadí jako číslo nebo řetězec nebo jiného typu. V seznamu výše v této stránce, operátory `_r` a `_t` slouží k definování nezpracovaná literálů:

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Literály nezpracovaných můžete zadat vlastní interpretace vstupní sekvence, která se liší od co by kompilátor provést. Například můžete definovat literál, který převede sekvenci `4.75987` do vlastního typu desetinné místo IEEE 754 číslo s plovoucí čárkou typ bodu. Literály nezpracovaných, jako jsou vařená literály, lze také provést ověření za kompilace vstupních řad.

### <a name="example-limitations-of-raw-literals"></a>Příklad: Omezení nezpracovaná literály

Operátoru nezpracovaného literálu a šablona operátoru literálu fungovat pouze pro integrální a s plovoucí desetinnou čárkou uživateli definované literály, jak je znázorněno v následujícím příkladu:

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```