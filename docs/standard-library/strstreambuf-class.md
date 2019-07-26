---
title: strstreambuf – třída
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: f24d8fe99bc211e026172e42669cf5e430ad31e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459081"
---
# <a name="strstreambuf-class"></a>strstreambuf – třída

Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků do a z sekvence prvků uložených v objektu pole typu **char** .

## <a name="syntax"></a>Syntaxe

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Poznámky

V závislosti na tom, jak je objekt vytvořen, lze přidělit, rozšířit a uvolnit podle potřeby pro přizpůsobení změn v sekvenci.

Objekt třídy `strstreambuf` ukládá několik bitů informací o režimu jako svůj `strstreambuf` režim. Tyto bity označují, zda řízená sekvence:

- Bylo přiděleno a je nutné je uvolnit nakonec.

- Lze upravovat.

- Je širším přidělením úložiště.

- Bylo zmrazeno a je třeba jej před zničením objektu nebo uvolněním (Pokud je přiděleno) jiným subjektem, než je objekt, zrušit zmrazením.

Kontrolované pořadí, které je zmrazeno, nelze změnit ani rozšířit, bez ohledu na stav těchto oddělených bitů režimu.

Objekt také ukládá ukazatele na dvě funkce, které řídí `strstreambuf` přidělení. Pokud jsou ukazatelé s hodnotou null, objekt navrhuje svou vlastní metodu přidělení a uvolnění úložiště pro řízenou sekvenci.

> [!NOTE]
> Tato třída je zastaralá. Místo toho zvažte použití [stringbuf –](../standard-library/sstream-typedefs.md#stringbuf) nebo [wstringbuf –](../standard-library/sstream-typedefs.md#wstringbuf) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[strstreambuf](#strstreambuf)|Vytvoří objekt typu `strstreambuf`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[uvolnění](#freeze)|Způsobí, že vyrovnávací paměť datového proudu nebude k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.|
|[overflow](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce, která se pokusí vrátit prvek do vstupního datového proudu a následně jej nastavit na aktuální prvek (ukazuje na další ukazatel).|
|[pcount](#pcount)|Vrátí počet prvků zapsaných do řízené sekvence.|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené streamy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené streamy.|
|[str](#str)|Volání [](#freeze)se zablokují a pak vrátí ukazatel na začátek řízené sekvence.|
|[podtečení](#underflow)|Chráněná virtuální funkce pro extrakci aktuálního prvku ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<strstream >

**Obor názvů:** std

## <a name="freeze"></a>strstreambuf:: zmrazit

Způsobí, že vyrovnávací paměť datového proudu nebude k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**Logická** hodnota označující, zda má být datový proud zmrazen.

### <a name="remarks"></a>Poznámky

Pokud má *_Freezeit* hodnotu true, funkce změní uložený `strstreambuf` režim tak, aby se kontrolované pořadí zablokované. V opačném případě se řízená sekvence nezmrazují.

[str](#str) implikuje `freeze`.

> [!NOTE]
> Zmrazená vyrovnávací paměť nebude uvolněna během `strstreambuf` zničení. Vyrovnávací paměť je nutné uvolnit před uvolněním, aby nedošlo k nevracení paměti.

### <a name="example"></a>Příklad

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="overflow"></a>strstreambuf:: přetečení

Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který má být vložen do vyrovnávací paměti `EOF`, nebo.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `EOF`se. V opačném případě, pokud  *\_meta* == `EOF`, vrátí jinou hodnotu `EOF`než. V opačném případě vrátí hodnotu  *\_meta*.

### <a name="remarks"></a>Poznámky

`EOF`Pokud  *\_se meta* ! =, chráněná virtuální členská funkce se pokusí vložit element `(char)_Meta` do výstupní vyrovnávací paměti. To lze provést různými způsoby:

- Pokud je k dispozici pozice pro zápis, může prvek Uložit do pozice pro zápis a zvýšit další ukazatel pro výstupní vyrovnávací paměť.

- Pokud uložený režim strstreambuf uvádí, že řízená sekvence je upravitelná, dá se nastavit jako nezmrazená, funkce může vytvořit pozici pro zápis přidělením nového pro výstupní vyrovnávací paměť. Rozšiřování výstupní vyrovnávací paměti tímto způsobem také rozšiřuje jakoukoli přidruženou vstupní vyrovnávací paměť.

## <a name="pbackfail"></a>strstreambuf::p neúspěšného selhání

Chráněná virtuální členská funkce, která se pokusí vrátit prvek do vstupního datového proudu a poté nastaví aktuální prvek (ukazuje na další ukazatel).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který má být vložen do vyrovnávací paměti `EOF`, nebo.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `EOF`se. V opačném případě, pokud  *\_meta* == `EOF`, vrátí jinou hodnotu `EOF`než. V opačném případě vrátí hodnotu  *\_meta*.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí vrátit prvek do vstupní vyrovnávací paměti a poté jej nastavit na aktuální prvek (ukazuje na další ukazatel).

Je-li  *\_meta* == , element pro zpětný zápis je efektivně ten, který je již v datovém proudu před aktuálním prvkem.`EOF` V opačném případě je tento prvek `ch = (char)_Meta`nahrazen. Funkce může vložit element zpět různými způsoby:

- Pokud je k dispozici putback pozice a element, na který se ukládá `ch`, se rovná, může snížit další ukazatel pro vstupní vyrovnávací paměť.

- Pokud je k dispozici putback pozice a pokud režim strstreambuf říká kontrolované sekvenci, může funkce ukládat `ch` do putback pozice a snížit další ukazatel pro vstupní vyrovnávací paměť.

## <a name="pcount"></a>strstreambuf: počet:p

Vrátí počet prvků zapsaných do řízené sekvence.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků zapsaných do řízené sekvence.

### <a name="remarks"></a>Poznámky

Konkrétně, pokud je [pptr](../standard-library/basic-streambuf-class.md#pptr) ukazatel s hodnotou null, vrátí funkce hodnotu nula. V opačném případě `pptr`vrátí  -  [pbase](../standard-library/basic-streambuf-class.md#pbase).

### <a name="example"></a>Příklad

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="seekoff"></a>strstreambuf:: seekoff

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené streamy.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice pro hledání vzhledem k *_Way*.

*_Way*\
Výchozí bod pro operace posunu. Možné hodnoty najdete v tématu [seekdir](../standard-library/ios-base-class.md#seekdir) .

*_Which*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce proběhne při změně buď na pozici datového proudu, nebo na obou místech, vrátí výslednou pozici streamu. V opačném případě selže a vrátí neplatnou pozici streamu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna změnu aktuální pozice pro řízené streamy. V případě objektu třídy strstreambuf se pozice datového proudu skládá čistě z posunu datového proudu. Nula odsazení určuje první prvek řízené sekvence.

Nová pozice je určena následujícím způsobem:

- Pokud `_Way == ios_base::beg`je nová pozice začátek datového proudu a *_Off*.

- Pokud `_Way == ios_base::cur`je nová pozice aktuální pozice datového proudu a *_Off*.

- Pokud `_Way == ios_base::end`je nová pozice koncem datového proudu plus *_Off*.

Pokud `_Which & ios_base::in` je hodnota nenulová a vstupní vyrovnávací paměť existuje, funkce změní další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud `_Which & ios_base::out` je také nenulová, `_Way != ios_base::cur`a výstupní vyrovnávací paměť existuje, funkce také nastaví další pozici, která se má zapsat, aby odpovídala další pozici ke čtení.

V opačném `_Which & ios_base::out` případě, pokud je nenulová a výstupní vyrovnávací paměť existuje, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. V opačném případě se operace umístění nezdařila. Aby operace umístění byla úspěšná, výsledná pozice v datovém proudu musí spadat do kontrolované sekvence.

## <a name="seekpos"></a>strstreambuf:: seekpos

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené streamy.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice pro hledání.

*_Which*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce proběhne při změně buď na pozici datového proudu, nebo na obou místech, vrátí výslednou pozici streamu. V opačném případě selže a vrátí neplatnou pozici streamu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte `pos_type(off_type(-1))`návratovou hodnotu hodnotou.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna změnu aktuální pozice pro řízené streamy. V případě objektu třídy strstreambuf se pozice datového proudu skládá čistě z posunu datového proudu. Nula odsazení určuje první prvek řízené sekvence. Nová pozice je určena pomocí *_Sp*.

Pokud `_Which` ios_base &  **:: in** je nenulové a vstupní vyrovnávací paměť existuje, funkce změní další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud `_Which`  &  je hodnotanenulováavýstupnívyrovnávacípaměťexistuje,funkcetakénastavídalšípozici,kterásemázapsat,abyodpovídaladalšípozicikečtení.`ios_base::out` V opačném `_Which` případě, pokud  &  `ios_base::out` je nenulová a výstupní vyrovnávací paměť existuje, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. V opačném případě se operace umístění nezdařila. Aby operace umístění byla úspěšná, výsledná pozice v datovém proudu musí spadat do kontrolované sekvence.

## <a name="str"></a>strstreambuf:: str

Volání [](#freeze)se zablokují a pak vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Neexistují žádné ukončující prázdné prvky, pokud jej explicitně nevložíte.

### <a name="example"></a>Příklad

Ukázku, která používá **str**, najdete v tématu [strstreambuf:: zmrazení](#freeze) .

## <a name="strstreambuf"></a>strstreambuf:: strstreambuf

Vytvoří objekt typu `strstreambuf`.

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Allocfunc*\
Funkce použitá k přidělení vyrovnávací paměti.

*výpočtu*\
Určuje délku vyrovnávací paměti, na kterou odkazuje *_Getptr*. Pokud *_Getptr* není argumentem (první konstruktorový formulář), navrhovaná velikost přidělení pro vyrovnávací paměti.

*_Freefunc*\
Funkce, která se používá k uvolnění vyrovnávací paměti.

*_Getptr*\
Vyrovnávací paměť použitá pro vstup.

*_Putptr*\
Vyrovnávací paměť použitá pro výstup.

### <a name="remarks"></a>Poznámky

První konstruktor ukládá ukazatel s hodnotou null ve všech ukazatelích řídících vstupní vyrovnávací paměť, výstupní vyrovnávací paměť a přidělení strstreambuf. Nastaví uložený režim strstreambuf, aby se řízená sekvence dá upravovat a rozšířila. Také přijímá *počet* jako navrhovanou počáteční velikost přidělení.

Druhý konstruktor se chová jako první, s tím rozdílem, že ukládá  *\_Allocfunc* jako ukazatel na funkci, která volá k přidělení úložiště a  *\_Freefunc* jako ukazatel na funkci, která je volána pro uvolnění tohoto úložiště.

Tři konstruktory:

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

také se chová jako první, s tím rozdílem, že `_Getptr` určuje objekt Array použitý pro uchování řízené sekvence. (Proto nesmí být ukazatel s hodnotou null.) Počet elementů *N* v poli je určen následujícím způsobem:

- If (`count` > 0); pak *N* `count`.

- If (`count` = = 0); Then *N* je `strlen`(( **const** `char` * `_Getptr` )).

- If (`count` < 0); pak *N* je **INT_MAX**.

Pokud `_Putptr` je ukazatel s hodnotou null, funkce vytvoří pouze vstupní vyrovnávací paměť spuštěním:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

V opačném případě vytvoří vstupní i výstupní vyrovnávací paměť spuštěním:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

V takovém případě `_Putptr` musí být v intervalu [ `_Getptr`, `_Getptr`  +  *N*].

Nakonec tři konstruktory:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

vše se chová stejně jako:

```cpp
streambuf((char *)_Getptr, count);
```

s tím rozdílem, že uložený režim neumožňuje upravovat ani měnitelné sekvence.

## <a name="underflow"></a>strstreambuf:: subflow

Chráněná virtuální funkce pro extrakci aktuálního prvku ze vstupního datového proudu.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `EOF`se. V opačném případě vrátí aktuální prvek ve vstupním datovém proudu, který je převeden tak, jak je popsáno výše.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna extrahování aktuálního prvku `ch` ze vstupní vyrovnávací paměti, následnému posunutí aktuálního umístění datového proudu a vrácení prvku jako (`int`) (`unsigned char`) () () **ch**. Může tak učinit pouze jedním ze způsobů: Pokud je dostupná pozice pro čtení, přebírá `ch` se jako element uložený na pozici pro čtení a předává další ukazatel pro vstupní vyrovnávací paměť.

## <a name="see-also"></a>Viz také:

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
