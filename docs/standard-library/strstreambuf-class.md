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
ms.openlocfilehash: 75c9a96b727ef60280055536296f850f492d16ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412277"
---
# <a name="strstreambuf-class"></a>strstreambuf – třída

Popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z pořadí prvků uložených v **char** objektu array.

## <a name="syntax"></a>Syntaxe

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Poznámky

V závislosti na tom, jak je objekt vytvořen může být přiděleny, rozšířit a uvolnění podle potřeby a vyřešit tak změny v pořadí.

Objekt třídy `strstreambuf` ukládá několik bits informace o režimu jako jeho `strstreambuf` režimu. Tyto bity označují, zda řízenou sekvenci:

- Byl přidělen a musí být nakonec uvolněna.

- Je upravitelné.

- Je možné rozšířit změna přidělení úložiště.

- Je zmrazen a proto musí být subjektem než objekt zmrazen předtím, než je objekt zničen, nebo uvolnění (je-li přidělit).

Nelze změnit ani rozšířené, bez ohledu na stav těchto samostatný režim bitů řízené sekvence, která je zmrazen.

Objekt také uchovává ukazatele na dvě funkce, které řídí `strstreambuf` přidělení. Pokud jsou ukazatelé s hodnotou null, objekt devises své vlastní metody přidělení a uvolnění úložiště řízené sekvence.

> [!NOTE]
> Tato třída je zastaralá. Zvažte použití [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) nebo [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) místo.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[strstreambuf –](#strstreambuf)|Vytvoří objekt typu `strstreambuf`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[zablokování](#freeze)|Způsobí, že vyrovnávací paměť datového proudu do nedostupný prostřednictvím operací vyrovnávací paměť datového proudu.|
|[overflow](#overflow)|Chráněné virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce, který se pokusí vložit element zpět do vstupního datového proudu a proveďte aktuálního elementu (ukazuje další ukazatel).|
|[pcount](#pcount)|Vrátí počet prvků zapsaných pro řízenou sekvenci.|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce, který se pokouší změnit aktuální pozice řízené datových proudů.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce, který se pokouší změnit aktuální pozice řízené datových proudů.|
|[str](#str)|Volání [ukotvit](#freeze)a vrátí ukazatel na začátek řízené sekvence.|
|[underflow](#underflow)|Chráněné virtuální funkce se extrahovat aktuálního elementu ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream – >

**Namespace:** std

## <a name="freeze"></a>  strstreambuf::freeze

Způsobí, že vyrovnávací paměť datového proudu do nedostupný prostřednictvím operací vyrovnávací paměť datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*<br/>
A **bool** označující, zda chcete datového proudu k zmrazit.

### <a name="remarks"></a>Poznámky

Pokud *_Freezeit* má hodnotu true, funkce mění uloženou `strstreambuf` režimu, aby zmrazené řízené sekvence. Jinak umožní řízené sekvence není zmrazen.

[Str](#str) znamená `freeze`.

> [!NOTE]
> Zmrazené vyrovnávací paměť se neuvolní během `strstreambuf` zničení. Vyrovnávací paměť musí uvolnit předtím, než je uvolněn aby se zabránilo nevrácení paměti.

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

## <a name="overflow"></a>  strstreambuf::Overflow

Chráněné virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo `EOF`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `EOF`. Jinak, pokud  *\_Meta* == `EOF`, vrátí některá z hodnot jiných než `EOF`. V opačném případě vrátí  *\_Meta*.

### <a name="remarks"></a>Poznámky

Pokud  *\_Meta* ! = `EOF`, chráněná virtuální členská funkce se pokusí vložit element `(char)_Meta` do výstupní vyrovnávací paměť. To lze provést různými způsoby:

- Pokud pozici zápisu je k dispozici, můžete uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.

- Pokud je režim uložené strstreambuf – zobrazeno řízené sekvence je upravitelná Dal a ne zmrazené, funkce zpřístupnit pozici zápisu přidělením nové pro výstupní vyrovnávací paměť. Rozšíření do vyrovnávací paměti výstupních tímto způsobem rozšiřuje také všechny přidružené vstupní vyrovnávací paměť.

## <a name="pbackfail"></a>  strstreambuf::pbackfail

Chráněná virtuální členská funkce, která se pokusí vrátit elementu do vstupního datového proudu a pak jej aktuálního elementu (ukazuje další ukazatel).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo `EOF`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `EOF`. Jinak, pokud  *\_Meta* == `EOF`, vrátí některá z hodnot jiných než `EOF`. V opačném případě vrátí  *\_Meta*.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí vrátit elementu do vstupní vyrovnávací paměť a nastavte ji aktuálního elementu (ukazuje další ukazatel).

Pokud  *\_Meta* == `EOF`, elementu, který chcete vložit zpět je v podstatě je již ve službě stream před aktuální prvek. V opačném případě se nahrazuje tento prvek `ch = (char)_Meta`. Funkci lze vrátit zpět element různými způsoby:

- Pokud putback – pozice je k dispozici a element v ní uloženy při porovnání rovna `ch`, je snížení další ukazatele pro vstupní vyrovnávací paměť.

- Pokud putback – pozice je k dispozici, a pokud režimu strstreambuf – uvádí, že je upravitelná řízené sekvence, můžete uložit funkce `ch` do pozice putback – a snížení další ukazatele pro vstupní vyrovnávací paměť.

## <a name="pcount"></a>  strstreambuf::pcount

Vrátí počet prvků zapsaných pro řízenou sekvenci.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet počet zapsaných pro řízenou sekvenci prvků.

### <a name="remarks"></a>Poznámky

Konkrétně Pokud [pptr –](../standard-library/basic-streambuf-class.md#pptr) je ukazatel s hodnotou null, vrátí funkce hodnotu nula. V opačném případě vrátí `pptr`  -  [pbase –](../standard-library/basic-streambuf-class.md#pbase).

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

## <a name="seekoff"></a>  strstreambuf::seekoff

Chráněná virtuální členská funkce, který se pokouší změnit aktuální pozice řízené datových proudů.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Pozice hledání pro relativně *_Way*.

*_Way*<br/>
Výchozí bod pro operace. Zobrazit [seekdir](../standard-library/ios-base-class.md#seekdir) možných hodnot.

*_Which*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje v změna buď nebo obojí datového proudu pozic, vrátí pozici výsledný datový proud. V opačném případě selže a vrátí pozici neplatný datový proud.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors ke změně aktuální pozice řízené datových proudů. Pro objekt strstreambuf – třída pozici v datovém proudu se skládá čistě posun datového proudu. Posunutí nula označí první prvek řízené sekvence.

Na nové pozici je stanoven následujícím způsobem:

- Pokud `_Way == ios_base::beg`, na nové pozici je začátku datového proudu plus *_Off*.

- Pokud `_Way == ios_base::cur`, na nové pozici, je aktuální pozici v datovém proudu plus *_Off*.

- Pokud `_Way == ios_base::end`, na nové pozici je konec datového proudu plus *_Off*.

Pokud `_Which & ios_base::in` je nenulová a neexistuje vstupní vyrovnávací paměť, funkce mění na další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud `_Which & ios_base::out` je nenulová `_Way != ios_base::cur`a existuje výstupní vyrovnávací paměť, funkce nastaví také další pozici pro zápis do odpovídá další pozici ke čtení.

Jinak, pokud `_Which & ios_base::out` je nenulová a existuje výstupní vyrovnávací paměť, funkce mění na další pozici pro zápis do výstupní vyrovnávací paměť. V opačném případě umístění operace se nezdaří. Umístění operace úspěšná musí být v řízené sekvenci od výsledný pozici v datovém proudu.

## <a name="seekpos"></a>  strstreambuf::seekpos

Chráněná virtuální členská funkce, který se pokouší změnit aktuální pozice řízené datových proudů.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Pozice k vyhledání pro.

*_Which*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje v změna buď nebo obojí datového proudu pozic, vrátí pozici výsledný datový proud. V opačném případě selže a vrátí pozici neplatný datový proud. Chcete-li zjistit, zda pozici v datovém proudu je neplatný, porovnejte návratovou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors ke změně aktuální pozice řízené datových proudů. Pro objekt strstreambuf – třída pozici v datovém proudu se skládá čistě posun datového proudu. Posunutí nula označí první prvek řízené sekvence. Je určená na nové pozici *_Sp*.

Pokud `_Which`  &  **ios_base::in** je nenulová a existuje vstupní vyrovnávací paměť, funkce mění na další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud `_Which`  &  `ios_base::out` je nenulová a existuje výstupní vyrovnávací paměť, funkce nastaví také další pozici pro zápis do odpovídá další pozici ke čtení. Jinak, pokud `_Which`  &  `ios_base::out` je nenulová a existuje výstupní vyrovnávací paměť, funkce mění na další pozici pro zápis do výstupní vyrovnávací paměť. V opačném případě umístění operace se nezdaří. Umístění operace úspěšná musí být v řízené sekvenci od výsledný pozici v datovém proudu.

## <a name="str"></a>  strstreambuf::str

Volání [ukotvit](#freeze)a vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Neexistuje žádný ukončujícího znaku null prvek, pokud explicitně vložit jednu.

### <a name="example"></a>Příklad

Zobrazit [strstreambuf::freeze](#freeze) ukázku, která používá **str**.

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

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

*_Allocfunc*<br/>
Funkce použitá k přidělení vyrovnávací paměti.

*Počet*<br/>
Určuje délku vyrovnávací paměti, na které odkazuje *_Getptr*. Pokud *_Getptr* není argument (první konstruktoru formuláře), navrhované přidělení velikost pro vyrovnávací paměti.

*_Freefunc*<br/>
Funkce použitá k uvolnění vyrovnávací paměti.

*_Getptr*<br/>
Vyrovnávací paměti použili pro vstup.

*_Putptr*<br/>
Vyrovnávací paměť pro výstup.

### <a name="remarks"></a>Poznámky

První konstruktor uloží ukazatel s hodnotou null v všechny ukazatele řízení vstupní vyrovnávací paměť, vyrovnávací paměti výstupních a strstreambuf – přidělení. Nastaví režim uložené strstreambuf – aby řízené sekvence upravitelnými a prodloužit. Přijímá také *počet* jako navrhované přidělení počáteční velikost.

Druhý konstruktor se chová jako první, s tím rozdílem, že ukládá  *\_Allocfunc* jako ukazatel na funkci, která má být volána pro přidělení úložiště a  *\_Freefunc* jako ukazatel do funkce volání k uvolnění tohoto úložiště.

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

také se chovat jako první, s tím rozdílem, že `_Getptr` označí objekt pole sloužící k uchování řízené sekvence. (Proto to nesmí být ukazatel s hodnotou null.) Počet prvků, které *N* v poli je stanoven následujícím způsobem:

- Pokud (`count` > 0), pak *N* je `count`.

- Pokud (`count` == 0), pak *N* je `strlen`(( **const** `char` *) `_Getptr` ).

- Pokud (`count` < 0), pak *N* je **INT_MAX**.

Pokud `_Putptr` je ukazatel s hodnotou null, funkce vytvoří pouze vstupní vyrovnávací paměť spuštěním:

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

V opačném případě určuje vstupní i výstupní vyrovnávací paměti spuštěním:

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

V takovém případě `_Putptr` musí být v rozsahu [ `_Getptr`, `_Getptr`  +  *N*].

Nakonec tři konstruktory:

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

všechny se chová stejně jako:

```cpp
streambuf((char *)_Getptr, count);
```

s tím rozdílem, že uložené režimu díky řízenou sekvenci lze měnit ani prodloužit.

## <a name="underflow"></a>  strstreambuf::underflow

Chráněné virtuální funkce se extrahovat aktuálního elementu ze vstupního datového proudu.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `EOF`. V opačném případě vrátí aktuální prvek ve vstupní datový proud, převést, jak je popsáno výše.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors extrahovat aktuálního elementu `ch` ze vstupní vyrovnávací paměť, pak přejděte aktuální pozici v datovém proudu a vrátí prvek jako (`int`) (`unsigned char`) **ch**. To lze provést pouze jedním ze způsobů: Pokud je k dispozici pozici pro čtení, trvá `ch` jako element uložené v pozici pro čtení a přejde na další ukazatele pro vstupní vyrovnávací paměť.

## <a name="see-also"></a>Viz také:

[streambuf –](../standard-library/streambuf-typedefs.md#streambuf)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
