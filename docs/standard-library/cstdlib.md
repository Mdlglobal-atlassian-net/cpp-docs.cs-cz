---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 0b4f24f50c78d9a079e2c7d0c8e3d3c5bfe952c2
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127219"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Obsahuje hlavičku \<standardní knihovny jazyka C Stdlib. h > a přidává přidružené názvy `std` do oboru názvů. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším propojením v záhlaví standardní knihovny jazyka C jsou deklarovány v `std` oboru názvů.

> [!NOTE]
> \<Stdlib. h > neobsahuje typ **wchar_t**.

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<cstdlib >

**Obor názvů:** std

## <a name="namespace-and-macros"></a>Obor názvů a makra

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Jenom Exposition funkce

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Funkce spuštění a ukončení

|Funkce|Popis|
|-|-|
|[_Exit](#_exit)|Ukončí program bez použití destruktorů nebo registrovaných funkcí.|
|[abort](#abort)|Ukončí program bez použití destruktorů.|
|[atexit](#atexit)|Zaregistruje funkci pro ukončení programu.|
|[exit](#exit)|Zničí objekty pomocí vlákna a statického úložiště a potom vrátí ovládací prvek.|
|[at_quick_exit](#at_quick_exit)|Registruje funkci bez argumentů pro ukončení programu.|
|[quick_exit](#quick_exit)|Zaregistruje funkci s zachované objekty pro ukončení programu.|
|[getenv](#getenv)|Viz Referenční dokumentace standardní knihovny jazyka C.|
|[souborů](#system)|Viz Referenční dokumentace standardní knihovny jazyka C.|

### <a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Poznámky

Program je ukončen bez provádění destruktorů pro objekty automatického, vlákna nebo statického trvání úložiště a bez volání funkcí předaných do `atexit()`. Funkce `_Exit` je bezpečná pro signál.

### <a name="abort"></a>přerušit

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Poznámky

Program je ukončen bez provádění destruktorů pro objekty automatického, vlákna nebo statického trvání úložiště a bez volání funkcí předaných do `atexit()`. Funkce `abort` je bezpečná pro signál.

### <a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Návratová hodnota

Nula, pokud je registrace úspěšná, nenulová, pokud selže.

#### <a name="remarks"></a>Poznámky

Funkce registruje funkci *Func*, která je volána bez argumentů při `quick_exit` volání metody. `at_quick_exit()` Volání `at_quick_exit()` , které se nestane, se `quick_exit` nemusí zdařit, dokud nebudou všechna volání úspěšná. `at_quick_exit()` Funkce nezavádí data rasy. Pořadí registrace může být neurčitelné, `at_quick_exit` Pokud bylo voláno z více než jednoho vlákna. Vzhledem `at_quick_exit` k tomu, že registrace `atexit` se liší od registrací, aplikace mohou vyžadovat volání registračních funkcí pomocí stejného argumentu. MSVC podporuje registraci alespoň 32 funkcí.

### <a name="atexit"></a>atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Poznámky

Funkce registrují funkci, na kterou odkazuje funkce Func na volání bez argumentů při normálním ukončení programu. `atexit()` Volání `atexit()` , které neproběhne před `exit()` voláním, nemusí být úspěšné. `atexit()` Funkce nezavádí data rasy.

#### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud je registrace úspěšná, nenulová, pokud selže.

### <a name="exit"></a>akci

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Poznámky

Nejprve objekty s dobou trvání úložiště vlákna a související s aktuálním vláknem jsou zničeny.

Dále objekty s trváním statického úložiště jsou zničeny a jsou volány funkce zaregistrované voláním `atexit` . Automatické objekty nejsou při `exit()` volání zničeny. Pokud ovládací prvek opustí registrovanou funkci volanou `exit` v důsledku toho, že funkce neposkytne obslužnou rutinu pro `std::terminate()` vyvolanou výjimku, je volána. Funkce se volá jednou pro každé zaregistrování. Objekty s automatickým trváním úložiště jsou zničeny v programu `main` , jehož funkce neobsahuje žádné automatické objekty a provádí `exit()`volání. Ovládací prvek lze přenést přímo do takové `main` funkce vyvoláním výjimky, která je zachycena v. `main`

V dalším kroku jsou všechny otevřené datové proudy jazyka c (jak jsou vyvolány signatury funkce deklarované v \<cstdio >) s nezapsanými daty uloženými do vyrovnávací paměti vyprázdněny, všechny otevřené datové proudy jazyka c jsou uzavřeny a všechny soubory vytvořené voláním `tmpfile()` budou odebrány.

Nakonec je ovládací prvek vrácen do hostitelského prostředí. Pokud je *stav* nula nebo EXIT_SUCCESS, je vrácena implementace definovaná formou úspěšného ukončení stavu. MSVC vrací hodnotu nula. Pokud je *stav* EXIT_FAILURE, MSVC vrátí hodnotu 3. V opačném případě MSVC vrátí hodnotu parametru *status* .

### <a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Poznámky

Obecně `at_quick_exit` jsou funkce registrované voláními volány v obráceném pořadí jejich registrace. Toto pořadí se nevztahuje na funkce zaregistrované po volání jiných registrovaných funkcí. Po `quick_exit` volání nejsou zničeny žádné objekty. Pokud ovládací prvek opustí registrovanou funkci volanou `quick_exit` v důsledku toho, že funkce neposkytne obslužnou rutinu pro `std::terminate()` vyvolanou výjimku, je volána. Funkce, která je `at_quick_exit` zaregistrována prostřednictvím, je vyvolána `quick_exit`vláknem, který volá, což může být jiné vlákno než ta, která ho zaregistrovala. To znamená, že registrované funkce by neměly spoléhat na identitu objektů, které mají dobu trvání úložiště vlákna. Po volání registrovaných funkcí `quick_exit` , `_Exit(status)`volání. Standardní vyrovnávací paměti souborů nejsou vyprázdněny. Funkce `quick_exit` je bezpečná pro signál, pokud jsou funkce zaregistrované v `at_quick_exit` .

### <a name="system"></a>souborů

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Funkce přidělování paměti

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C. MSVC nepodporuje `aligned_alloc` funkci. C11 určený `aligned_alloc()` způsobem, který je nekompatibilní s `free()`implementací Microsoft, konkrétně, která `free()` musí být schopná zvládnout vysoce zarovnané přidělení.

## <a name="numeric-string-conversions"></a>Převody číselných řetězců

```cpp
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C.

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>Vícebajtové a velké řetězcové funkce a funkce pro převod znaků

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C.

## <a name="algorithm-functions"></a>Funkce algoritmu

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C.

## <a name="low-quality-random-number-generation-functions"></a>Funkce pro generování náhodných čísel typu nízká kvalita

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C.

## <a name="absolute-values"></a>Absolutní hodnoty

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C.

## <a name="integer-division"></a>Dělení celého čísla

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku určenou ve standardní knihovně jazyka C.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
