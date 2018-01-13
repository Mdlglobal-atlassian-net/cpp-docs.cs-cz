---
title: "Uživateli definované literály (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a461f4ca384585008ccf47fa2bfda91d36e724ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-literals--c"></a>Uživateli definované literály (C++)
Existují pět hlavních kategorií literálů: celé číslo, znak, s plovoucí desetinnou čárkou, řetězec, logická hodnota a ukazatel.  Počínaje C++ 11, můžete definovat vlastní literály podle těchto kategorií pro účely poskytování syntaktické zástupce pro běžné idioms a zvýšit zabezpečení typů. Řekněme například, že máte třídu vzdálenost. Můžete definovat literál pro kilometrech a další pro paliva a motivovat uživatele explicitní měrné jednotky jednoduše napsáním: automatické d = 42.0_km nebo auto d = 42.0_mi. Neexistuje žádné výhody výkonu nebo nevýhody k uživateli definované literály; jsou to především pro usnadnění práce nebo pro odvození typu v čase kompilace. Standardní knihovna má uživateli definované literály std:string, std::complex a jednotky v čas a dobu trvání operace v \<typu chrono > hlavičky:  
  
```  
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)  
    std::string str = "hello"s + "World"s;  // Standard Library <string> UDL  
    complex<double> num =   
        (2.0 + 3.01i) * (5.0 + 4.3i);       // Standard Library <complex> UDL  
    auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs  
```  
  
## <a name="user-defined-literal-operator-signatures"></a>Uživatelem definované literálu operátor podpisy  
 Implementace literál uživatelem definované definováním `operator""` v oboru názvů s jedním z následujících podob:  
  
```  
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
  
 Operátor názvy v předchozím příkladu jsou zástupné symboly pro jakýkoli název můžete zadat; vedoucí znak podtržítko je však vyžaduje. (Pouze standardní knihovna je povolena k definování literály bez podtržítko). Návratový typ je, kde můžete přizpůsobit převod nebo jiná operace, která provádí literál. Kromě toho některé z těchto operátorů může být definováno jako `constexpr`.  
  
## <a name="cooked-literals"></a>Vařené literály  
 Ve zdroji code žádné literál, zda vlastní nebo není je v podstatě pořadí alfanumerické znaky, jako například `101`, nebo `54.7`, nebo `"hello"` nebo `true`. Kompilátor interpretuje pořadí jako celé číslo, float, const char\* řetězec a tak dále. Uživatelem definované literál, který přijme jako vstup, ať zadejte kompilátoru přiřazené literálovou hodnotou se nazývá neformálně *vařené literál*. Všechny operátory výše, s výjimkou `_r` a `_t` jsou vařená literály. Například literál `42.0_km` by vytvořit vazbu na operátor s názvem _km, který měl podobné _b a literálové podpis `42_km` by vytvořit vazbu na operátor podobná _a podpisem.  
  
 Následující příklad ukazuje, jak uživateli definované literály může podporovat volající byli explicitní o jejich vstup. K vytvoření `Distance`, musí uživatel explicitně zadat kilometrech nebo miles pomocí odpovídající uživatelem definované literál. Samozřejmě můžete také dosažení stejného výsledku jinými způsoby, ale uživateli definované literály jsou méně podrobný než alternativ.  
  
```  
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
  
 Všimněte si, že číslo literálu musíte použít datový typ decimal, jinak by číslo interpretovat jako celé číslo a typ nebude kompatibilní s operátorem. Všimněte si, že pro plovoucí vstupní bod, musí být typu `long double`a pro integrální typy musí být `long long`.  
  
## <a name="raw-literals"></a>Nezpracovaná literály  
 V nezpracovaných literál uživatelem definované operátor, který definujete akceptuje literálové jako pořadí hodnot typu char a je na vás interpretovat jako číslo nebo řetězec nebo jiný typ tohoto pořadí. V seznamu operátory uvedené dříve v této stránce `_r` a `_t` lze použít k definování nezpracovaná literály:  
  
```  
ReturnType operator "" _r(const char*);              // Raw literal operator  
template<char...> ReturnType operator "" _t();       // Literal operator template  
```  
  
 Nezpracovaná literály můžete zadat vlastní interpretace vstupní pořadí, než co by kompilátor provedl. Můžete například definovat literál, který převádí sekvenci `4.75987` do vlastního typu Decimal místo IEEE 754 plovoucí typ bodu. Nezpracovaná literály jako z literály, lze také použít k provedení ověření kompilaci vstupní pořadí.  
  
### <a name="example"></a>Příklad  
  
### <a name="limitations-of-raw-literals"></a>Omezení nezpracovaná literály  
 Nezpracovaná literálu operátor a literálu operátor šablony fungovat pouze pro integrální a s plovoucí desetinnou čárkou uživateli definované literály, jak je znázorněno v následujícím příkladu:  
  
```  
#include <cstddef>  
#include <cstdio>  
  
void operator "" _dump(unsigned long long int lit)  { printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit); };  // Literal operator for user-defined INTEGRAL literal  
void operator "" _dump(long double lit)             { printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit); };  // Literal operator for user-defined FLOATING literal  
void operator "" _dump(char lit)                    { printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(wchar_t lit)                 { printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(char16_t lit)                { printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(char32_t lit)                { printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(const     char* lit, size_t) { printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit); };  // Literal operator for user-defined STRING literal  
void operator "" _dump(const  wchar_t* lit, size_t) { printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit); };  // Literal operator for user-defined STRING literal  
void operator "" _dump(const char16_t* lit, size_t) { printf("operator \"\" _dump(const char16_t*, size_t):\n"                  ); };  // Literal operator for user-defined STRING literal  
void operator "" _dump(const char32_t* lit, size_t) { printf("operator \"\" _dump(const char32_t*, size_t):\n"                  ); };  // Literal operator for user-defined STRING literal  
void operator "" _dump_raw(const char* lit)         { printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit); };  // Raw literal operator  
  
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
    // 'A'_dump_raw;               // There is no raw literal operator or literal operator template support on this type  
    //L'B'_dump_raw;              // There is no raw literal operator or literal operator template support on this type  
    //u'C'_dump_raw;              // There is no raw literal operator or literal operator template support on this type  
    //U'D'_dump_raw;              // There is no raw literal operator or literal operator template support on this type  
    //  "Hello World"_dump_raw;   // There is no raw literal operator or literal operator template support on this type  
    // L"Wide String"_dump_raw;   // There is no raw literal operator or literal operator template support on this type  
    //u8"UTF-8 String"_dump_raw;   // There is no raw literal operator or literal operator template support on this type  
    // u"UTF-16 String"_dump_raw;  // There is no raw literal operator or literal operator template support on this type  
    // U"UTF-32 String"_dump_raw;  // There is no raw literal operator or literal operator template support on this type  
}  
/*****  
Output:  
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
*****/  
  
```