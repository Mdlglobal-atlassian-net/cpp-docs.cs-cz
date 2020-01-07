---
title: Uživatelsky definované literály (C++)
ms.date: 12/10/2019
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: 31b8f1dfb261839c04a6829132975ada9c09d619
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301298"
---
# <a name="user-defined-literals"></a>Literály definované uživatelem

Existuje pět hlavních kategorií literálů v C++: celé číslo, znak, plovoucí desetinná čárka, řetězec, logická hodnota a ukazatel.  Počínaje C++ 11 můžete definovat vlastní literály založené na těchto kategoriích a poskytnout tak syntaktické zkratky pro běžné idiomy a zvýšit bezpečnost typů. Řekněme například, že máte třídu Distance. Můžete definovat literál pro kilometry a další pro kilometry a povzbuzovat, aby uživatel byl explicitní o měrné jednotce, a to pouhým zápisem: auto d = 42.0_km nebo auto d = 42.0_mi. Uživatelsky definované literály nejsou žádné výhody nebo nevýhody výkonu. jsou primárně určeny pro pohodlí nebo pro odvození typu v době kompilace. Standardní knihovna má uživatelsky definované literály pro std: String, pro std:: Complex a pro jednotky v čase a dobu trvání operací v hlavičce \<Chrono >:

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Uživatelsky definované signatury operátoru literálu

Implementujete uživatelsky definovaný literál definováním **operátoru ""** v oboru názvů s jedním z následujících forem:

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Názvy operátorů v předchozím příkladu jsou zástupné symboly pro libovolný název, který zadáte; je však požadováno počáteční podtržítko. (Pouze standardní knihovna smí definovat literály bez podtržítka.) Návratový typ je místo, kde můžete přizpůsobit převod nebo jinou operaci, kterou literál provádí. Kterýkoli z těchto operátorů lze také definovat jako `constexpr`.

## <a name="cooked-literals"></a>Vařené literály

Ve zdrojovém kódu jakýkoliv literál bez ohledu na to, zda je uživatelsky definovaný nebo ne, sekvence alfanumerických znaků, například `101`nebo `54.7`nebo `"hello"` nebo `true`. Kompilátor interpretuje sekvenci jako celé číslo, float, const char\* řetězec atd. Uživatelsky definovaný literál, který přijímá jako vstup bez ohledu na typ, který je kompilátor přiřazený k hodnotě literálu, je neformálně známý jako *vařené literály*. Všechny operátory výše s výjimkou `_r` a `_t` jsou vařené literály. Například literální `42.0_km` by se navázalo na operátor s názvem _km, který měl signaturu podobný _b a literál `42_km` by měl vytvořit vazby k operátoru s signaturou podobnou _a.

Následující příklad ukazuje, jak uživatelsky definované literály mohou povzbudit volající, aby byli explicitní o jejich vstupu. Chcete-li vytvořit `Distance`, musí uživatel explicitně zadat kilometry nebo kilometry pomocí příslušného uživatelsky definovaného literálu. Samozřejmě můžete také dosáhnout stejného výsledku jiným způsobem, ale uživatelsky definované literály jsou méně podrobné, než alternativy.

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

Všimněte si, že číslo literálu musí používat desetinné číslo, jinak bude číslo interpretováno jako celé číslo a typ nebude kompatibilní s operátorem. Všimněte si také, že pro vstup s plovoucí desetinnou čárkou musí být typ **Long Double**a integrální typy musí být **dlouhé**.

## <a name="raw-literals"></a>Nezpracované literály

V nezpracovaném uživatelsky definovaném literálu operátor, který definujete, přijímá literál jako sekvenci hodnot typu char a je až na to, abyste tuto sekvenci interpretoval jako číslo nebo řetězec nebo jiný typ. V seznamu operátorů, které jsou uvedeny dříve na této stránce, `_r` a `_t` lze použít k definování nezpracovaných literálů:

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Nezpracované literály můžete použít k poskytnutí vlastní interpretace vstupní sekvence, která se liší od toho, co by kompilátor prováděl. Můžete například definovat literál, který převede `4.75987` sekvence na vlastní typ desetinné číslo namísto typu s plovoucí desetinnou čárkou standardu IEEE 754. Nezpracované literály, jako jsou vařené literály, lze také použít k provedení ověřování vstupních sekvencí při kompilaci.

### <a name="example-limitations-of-raw-literals"></a>Příklad: omezení nezpracovaných literálů

Nezpracovaný literálový operátor a šablona operátora literálu fungují pouze pro uživatelsky definované literály typu integrální a plovoucí desetinné čárky, jak je znázorněno v následujícím příkladu:

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
