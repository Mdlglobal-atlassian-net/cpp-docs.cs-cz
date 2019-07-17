---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 70e05ad734fa49ba8cb96e4bf83bc05b99c5f55c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246532"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Obsahuje hlavičku knihovny C Standard \<stdlib.h > a přidá názvy přidružené k `std` oboru názvů. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v hlavičce standardní knihovny jazyka C jsou deklarovány v `std` oboru názvů.

> [!NOTE]
> \<stdlib.h > neobsahuje typ **wchar_t**.

## <a name="requirements"></a>Požadavky

**Hlavička**: \<cstdlib – >

**Namespace:** std

## <a name="namespace-and-macros"></a>Namespace a makra

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

## <a name="exposition-only-functions"></a>Budeme pouze funkce

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Spuštění a ukončení funkce

|Funkce|Popis|
|-|-|
|[_Exit](#_exit)|Program se ukončí bez použití destruktorů nebo registrovaná funkce.|
|[abort](#abort)|Program se ukončí bez použití destruktorů.|
|[atexit](#atexit)|Registruje funkci pro ukončení programu.|
|[exit](#exit)|Zničí objekty se vlákno a statického úložiště, pak vrátí řízení.|
|[at_quick_exit](#at_quick_exit)|Registry funkce bez argumentů pro ukončení programu.|
|[quick_exit](#quick_exit)|Registruje funkci s zachovaných objekty pro ukončení programu.|
|[GETENV](#getenv)|Přehled standardní knihovny C.|
|[Systém](#system)|Přehled standardní knihovny C.|

### <a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Poznámky

Program se ukončí bez provádění destruktory pro objekty automaticky, vlákna nebo statickou dobu ukládání a volání funkcí předat `atexit()`. Funkce `_Exit` je signál typově bezpečné.

### <a name="abort"></a> Přerušení

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Poznámky

Program se ukončí bez provádění destruktory pro objekty automaticky, vlákna nebo statickou dobu ukládání a volání funkcí předat `atexit()`. Funkce `abort` je signál typově bezpečné.

### <a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Návratová hodnota

Nula v případě úspěšné registrace, nenulové Pokud selže.

#### <a name="remarks"></a>Poznámky

`at_quick_exit()` Funkce zaregistrovat funkci, na které odkazuje *func* volat bez argumentů při `quick_exit` je volána. Má tento parametr zadán, zda volání `at_quick_exit()` , který nemá dojít před všechna volání `quick_exit` proběhne úspěšně a `at_quick_exit()` funkce nezavádí data závodu. Pořadí registrace může být neurčitý Pokud `at_quick_exit` byla volána z více než jedno vlákno a od `at_quick_exit` registrace se liší od `atexit` registrace, aplikace je nutné volat obě funkce registrace se stejný argument. Implementace podporuje registraci funkce alespoň 32.

### <a name="atexit"></a> AtExit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Poznámky

`atexit()` Funkce zaregistrovat funkci, na které odkazuje *func* volat bez argumentů při ukončení programu normální. Má tento parametr zadán, zda volání `atexit()` , která nejsou provedeny před voláním `exit()` proběhne úspěšně a `atexit()` funkce nezavádí data závodu. Implementace podporuje registraci funkce alespoň 32.

#### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud se registrace podaří, nenulovou hodnotu, pokud se nezdaří.

### <a name="exit"></a> ukončení

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Poznámky

Nejprve objekty s dobou trvání úložiště vlákna a spojené s aktuálním vlákně nejsou zničeny.

V dalším kroku objekty s trváním statického úložiště jsou zničeny, a funkce zaregistrovaný voláním `atexit` jsou volány. Automatické objekty nejsou zničeny, v důsledku volání metody `exit()`. Pokud registrované funkci volanou třídou předá řízení `exit` protože neposkytuje funkce obslužnou rutinu pro vyvolanou výjimku `std::terminate()` musí být volána. Funkce je volána pro pokaždé, když je zaregistrovaný. Objekty s automatickým trváním úložiště jsou zničeny v programu, jehož hlavní funkce neobsahuje žádné automatické objekty a provede volání `exit()`. Ovládací prvek lze přenést přímo do hlavní funkce vyvoláním výjimky, která je zachycena ve funkci main.

V dalším kroku všechny otevřené C datové proudy (jako zprostředkována signatury funkce deklarované v <cstdio>) s nepsaná data ve vyrovnávací paměti jsou vyprázdněných, všechny otevřené C datové proudy jsou uzavřeny a všechny soubory vytvořených voláním `tmpfile()` se odeberou.

A konečně ovládací prvek se vrátí do hostitelského prostředí. Pokud stav může být nula nebo EXIT_SUCCESS, vrátí se definované implementací formu ukončení úspěšný stav. Pokud je stav EXIT_FAILURE, je vrácena definované implementací formu neúspěšné ukončení stav. V opačném případě vrátí stav, je definováno implementací.

### <a name="getenv"></a> GETENV

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Poznámky

Funkce registrovaných volání `at_quick_exit` jsou volány v obráceném pořadí jejich registraci, a s tím rozdílem, že funkce musí být volána po některé funkce, které již byla volána v době byl zaregistrován dříve zaregistrovali. Následkem volání nebude zničení objektů `quick_exit`. Pokud registrované funkci volanou třídou předá řízení `quick_exit` protože neposkytuje funkce obslužnou rutinu pro vyvolanou výjimku `std::terminate()` musí být volána. Funkce registrovat prostřednictvím `at_quick_exit` vyvolá vlákna, která volá `quick_exit`, což může být jiném vlákně než ten, který zaregistrovaný, proto zaregistrován funkce neměli byste tedy spoléhat na identitě objektů s dobou trvání úložiště vlákna. Po volání registrovaná funkcí `quick_exit` musí volat `_Exit(status)`. Standardní soubor vyrovnávací paměti se vyprázdní. Funkce `quick_exit` je signál typově bezpečný, když funkce zaregistrován ve službě `at_quick_exit` jsou.

### <a name="system"></a> Systém

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Funkce přidělení paměti

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
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

#### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku zadaný ve standardní knihovně jazyka C.

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Vícebajtový / široký řetězec a funkce pro převod znaků

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku zadaný ve standardní knihovně jazyka C.

## <a name="algorithm-functions"></a>Algoritmické funkce

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku zadaný ve standardní knihovně jazyka C.

## <a name="low-quality-random-number-generation-functions"></a>Funkce generování náhodných čísel nízké kvality

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku zadaný ve standardní knihovně jazyka C.

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
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Poznámky

Tyto funkce mají sémantiku zadaný ve standardní knihovně jazyka C.

## <a name="functions"></a>Funkce

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
