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
ms.openlocfilehash: 28399a1cd55407aadbc5d59e1e835892218ad0c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376614"
---
# <a name="strstreambuf-class"></a>strstreambuf – třída

Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků do a z posloupnosti prvků uložených v objektu **pole char.**

## <a name="syntax"></a>Syntaxe

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Poznámky

V závislosti na tom, jak je objekt vytvořen, může být přidělen, rozšířen a uvolněn podle potřeby přizpůsobit změny v pořadí.

Objekt třídy `strstreambuf` ukládá několik bitů informací `strstreambuf` o režimu jako jeho režim. Tyto bity označují, zda řízená sekvence:

- Byla přidělena a musí být uvolněna nakonec.

- Je upravitelný.

- Je rozšiřitelný přerozdělením úložiště.

- Byl zmrazen, a proto je třeba uvolnit před objekt je zničen nebo uvolněna (pokud je přidělena) jiným subjektem než objekt.

Řízenou sekvenci, která je zmrazena, nelze změnit ani rozšířit, bez ohledu na stav těchto samostatných bitů režimu.

Objekt také ukládá ukazatele na dvě `strstreambuf` funkce, které řídí přidělení. Pokud se jedná o ukazatele null, objekt navrhne vlastní metodu přidělování a uvolnění úložiště pro řízené sekvence.

> [!NOTE]
> Tato třída je zastaralá. Zvažte použití [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) nebo [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) místo.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[strstreambuf](#strstreambuf)|Vytvoří objekt typu `strstreambuf`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zmrazit](#freeze)|Způsobí, že vyrovnávací paměť datového proudu není k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.|
|[Přetečení](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce, která se pokusí vrátit prvek zpět do vstupního datového proudu a pak z něj udělat aktuální prvek (na který odkazuje další ukazatel).|
|[pcount](#pcount)|Vrátí počet počtu prvků zapsaných do řízené sekvence.|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[Str](#str)|Volání [zmrazit](#freeze)a potom vrátí ukazatel na začátek řízené sekvence.|
|[Podtečení](#underflow)|Chráněná virtuální funkce extrahovat aktuální prvek ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream>

**Obor názvů:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>strstreambuf::zmrazení

Způsobí, že vyrovnávací paměť datového proudu není k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**Bool** označující, zda chcete, aby byl datový proud zmrazen.

### <a name="remarks"></a>Poznámky

Pokud *je _Freezeit* true, funkce `strstreambuf` změní uložený režim tak, aby řízená sekvence zamrzla. V opačném případě způsobí, že řízená sekvence není zmrazena.

[str](#str) `freeze`znamená .

> [!NOTE]
> Zmrazená vyrovnávací paměť nebude `strstreambuf` během zničení uvolněna. Je nutné uvolnit vyrovnávací paměti před uvolněním, aby se zabránilo nevracení paměti.

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

## <a name="strstreambufoverflow"></a><a name="overflow"></a>strstreambuf:přetečení

Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak vložit do vyrovnávací paměti `EOF`nebo .

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být `EOF`úspěšná, vrátí . V opačném * \_* případě, pokud Meta == `EOF` `EOF`, vrátí jinou hodnotu než . V opačném * \_* případě vrátí Meta .

### <a name="remarks"></a>Poznámky

Pokud * \_Meta* `EOF`!= , chráněné virtuální členská `(char)_Meta` funkce se pokusí vložit prvek do výstupní vyrovnávací paměti. Může tak učinit různými způsoby:

- Pokud je k dispozici pozice zápisu, může uložit prvek do pozice zápisu a zvýšit další ukazatel pro výstupní vyrovnávací paměti.

- Pokud uložený režim strstreambuf říká, že řízená sekvence je upravitelná, rozšiřitelná a není zmrazena, funkce může zpřístupnit pozici zápisu přidělením nové pro výstupní vyrovnávací paměť. Rozšíření výstupní vyrovnávací paměti tímto způsobem také rozšiřuje všechny přidružené vstupní vyrovnávací paměti.

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>strstreambuf::pbackfail

Chráněná virtuální členská funkce, která se pokusí vrátit prvek zpět do vstupního datového proudu a poté jej provede aktuálním prvkem (na který odkazuje další ukazatel).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak vložit do vyrovnávací paměti `EOF`nebo .

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být `EOF`úspěšná, vrátí . V opačném * \_* případě, pokud Meta == `EOF` `EOF`, vrátí jinou hodnotu než . V opačném * \_* případě vrátí Meta .

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí vrátit prvek zpět do vstupní vyrovnávací paměti a potom jej učinit aktuálním prvkem (na který odkazuje další ukazatel).

Pokud * \_Meta* == `EOF`, prvek push back je efektivně ten, který již v datovém proudu před aktuální prvek. V opačném případě je `ch = (char)_Meta`tento prvek nahrazen . Funkce může vrátit prvek různými způsoby:

- Pokud putback pozice je k dispozici a prvek `ch`uložený tam porovnává rovná , může zmenšit další ukazatel pro vstupní vyrovnávací paměti.

- Pokud putback pozice je k dispozici a pokud strstreambuf režim říká, že `ch` řízené sekvence je upravitelný, funkce můžete uložit do putback pozice a snížení další ukazatel pro vstupní vyrovnávací paměti.

## <a name="strstreambufpcount"></a><a name="pcount"></a>strstreambuf::ppočet

Vrátí počet počtu prvků zapsaných do řízené sekvence.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet počet prvků zapsaných do řízené sekvence.

### <a name="remarks"></a>Poznámky

Konkrétně pokud [pptr](../standard-library/basic-streambuf-class.md#pptr) je ukazatel null, funkce vrátí nulu. V opačném `pptr`  - případě vrátí [pbase](../standard-library/basic-streambuf-class.md#pbase).

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

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>strstreambuf::seekoff

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice hledat vzhledem k *_Way*.

*_Way*\
Počáteční bod pro operace odsazení. Viz [seekdir](../standard-library/ios-base-class.md#seekdir) pro možné hodnoty.

*_Which*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje při změně jedné nebo obou pozic datového proudu, vrátí výslednou pozici datového proudu. V opačném případě selže a vrátí pozici neplatného datového proudu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se snaží změnit aktuální pozice pro řízené datové proudy. Pro objekt třídy strstreambuf pozice datového proudu se skládá čistě z posunu datového proudu. Posun nula označuje první prvek řízené sekvence.

Nová pozice je určena takto:

- Pokud `_Way == ios_base::beg`je nová pozice začátkem datového proudu plus *_Off*.

- Pokud `_Way == ios_base::cur`je nová pozice aktuální polohou datového proudu plus *_Off*.

- Pokud `_Way == ios_base::end`je nová pozice koncem datového proudu plus *_Off*.

Pokud `_Which & ios_base::in` je nenulová a vstupní vyrovnávací paměť existují, funkce změní další pozici ke čtení ve vstupní vyrovnávací paměti. Pokud `_Which & ios_base::out` je také `_Way != ios_base::cur`nenulová a výstupní vyrovnávací paměť existuje, funkce také nastaví další pozici pro zápis tak, aby odpovídala další pozici ke čtení.

V opačném `_Which & ios_base::out` případě, pokud je nenulová a výstupní vyrovnávací paměť existuje, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. V opačném případě se operace umístění nezdaří. Aby byla operace umístění úspěšná, musí být výsledná pozice datového proudu v řízené posloupnosti.

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>strstreambuf::seekpos

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice, o kterou se můžete snažit.

*_Which*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje při změně jedné nebo obou pozic datového proudu, vrátí výslednou pozici datového proudu. V opačném případě selže a vrátí pozici neplatného datového proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se snaží změnit aktuální pozice pro řízené datové proudy. Pro objekt třídy strstreambuf pozice datového proudu se skládá čistě z posunu datového proudu. Posun nula označuje první prvek řízené sekvence. Nová pozice je určena *_Sp*.

Pokud `_Which`  &  **ios_base::in** je nenulová a vstupní vyrovnávací paměť existuje, funkce změní další pozici ke čtení ve vstupní vyrovnávací paměti. `_Which`  &  Pokud `ios_base::out` je nenulová a výstupní vyrovnávací paměť existuje, funkce také nastaví další pozici pro zápis tak, aby odpovídala další pozici ke čtení. V opačném `_Which`  &  `ios_base::out` případě, pokud je nenulová a výstupní vyrovnávací paměť existuje, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. V opačném případě se operace umístění nezdaří. Aby byla operace umístění úspěšná, musí být výsledná pozice datového proudu v řízené posloupnosti.

## <a name="strstreambufstr"></a><a name="str"></a>strstreambuf::str

Volání [zmrazit](#freeze)a potom vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Neexistuje žádný ukončující element null, pokud jej explicitně nevložíte.

### <a name="example"></a>Příklad

Viz [strstreambuf::freeze](#freeze) pro vzorek, který používá **str**.

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>strstreambuf::strstreambuf

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
Funkce slouží k přidělení vyrovnávací paměti.

*Počet*\
Určuje délku vyrovnávací paměti, na kterou se *_Getptr*. Pokud *_Getptr* není argument (první forma konstruktoru), navrhovaná velikost přidělení pro vyrovnávací paměti.

*_Freefunc*\
Funkce slouží k uvolnění vyrovnávací paměti.

*_Getptr*\
Vyrovnávací paměť používaná pro vstup.

*_Putptr*\
Vyrovnávací paměť použitá pro výstup.

### <a name="remarks"></a>Poznámky

První konstruktor ukládá nulový ukazatel ve všech ukazatelích ovládajících vstupní vyrovnávací paměť, výstupní vyrovnávací paměť a přidělení strstreambuf. Nastavuje uložený režim strstreambuf tak, aby řízená sekvence byla modifikovatelná a rozšiřitelná. Také přijímá *počítat* jako navrhované počáteční velikost přidělení.

Druhý konstruktor se chová jako první, s tím rozdílem, že ukládá * \_Allocfunc* jako ukazatel na funkci pro volání přidělení úložiště a * \_Freefunc* jako ukazatel na funkci pro volání k uvolnění tohoto úložiště.

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

také chovat jako první, `_Getptr` kromě toho, že označuje objekt pole slouží k uložení řízené sekvence. (Proto nesmí být ukazatel null.) Počet prvků *N* v poli je určen takto:

- Pokud`count` ( > 0), `count`pak *N* je .

- Pokud`count` ( == 0), `strlen`pak *N* je `_Getptr` ( ( **const** `char` *) ).

- Pokud`count` ( < 0), pak *N* je **INT_MAX**.

Pokud `_Putptr` je ukazatel null, funkce vytvoří pouze vstupní vyrovnávací paměť spuštěním:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

V opačném případě vytvoří vstupní i výstupní vyrovnávací paměti spuštěním:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

V tomto `_Putptr` případě musí být `_Getptr`v `_Getptr`  + intervalu [ , *N*].

Nakonec tři konstruktory:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

všichni se chovají stejně jako:

```cpp
streambuf((char *)_Getptr, count);
```

s tím rozdílem, že uložený režim činí řízenou sekvenci ani modifikovatelnou, ani rozšiřitelnou.

## <a name="strstreambufunderflow"></a><a name="underflow"></a>strstreambuf::podtočení

Chráněná virtuální funkce extrahovat aktuální prvek ze vstupního datového proudu.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být `EOF`úspěšná, vrátí . V opačném případě vrátí aktuální prvek ve vstupním datovém proudu, převedený, jak je popsáno výše.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se `ch` snaží extrahovat aktuální prvek ze vstupní vyrovnávací paměti,`int`potom`unsigned char`posunout aktuální pozici datového proudu a vrátit prvek jako ( )( ) **ch**. Může tak učinit pouze jedním způsobem: pokud je k `ch` dispozici pozice pro čtení, trvá jako prvek uložený v pozici pro čtení a posune další ukazatel pro vstupní vyrovnávací paměti.

## <a name="see-also"></a>Viz také

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
