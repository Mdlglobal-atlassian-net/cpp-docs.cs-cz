---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 03afb777dc3926284cf0dc625e94a716ecdf5413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375348"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje objekty, které řídí čtení a zápis do standardních datových proudů. To to zahrnuje často pouze záhlaví, které potřebujete udělat vstup a výstup z programu C++.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

> [!NOTE]
> \<Knihovna> iostream `#include <ios>` `#include <streambuf>`používá `#include <istream>`příkazy , , a. `#include <ostream>`

## <a name="remarks"></a>Poznámky

Objekty spadají do dvou skupin:

- [cin](#cin), [cout](#cout), [cerr](#cerr)a [ucpat](#clog) jsou byte orientované, dělat konvenční byte-at-a-time převody.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr), a [wclog](#wclog) jsou široce orientované, překládání do a z široké znaky, které program manipuluje interně.

Jakmile uděláte určité operace v datovém proudu, jako je například standardní vstup, nelze provést operace s jinou orientací na stejném datovém proudu. Proto program nemůže pracovat zaměnitelně na obou [cin](#cin) a [wcin](#wcin), například.

Všechny objekty deklarované v tomto záhlaví sdílejí zvláštní vlastnost – můžete předpokládat, že jsou \<vytvořeny před všechny statické objekty, které definujete, v jednotce překladu, která obsahuje> iostream. Stejně tak můžete předpokládat, že tyto objekty nejsou zničeny před destruktory pro všechny takové statické objekty, které definujete. (Výstupní datové proudy jsou však vyprázdněny během ukončení programu.) Proto můžete bezpečně číst nebo zapisovat do standardních datových proudů před spuštěním programu a po ukončení programu.

Tato záruka však není univerzální. Statický konstruktor může volat funkci v jiné jednotce překladu. Volaná funkce nemůže předpokládat, že objekty deklarované v této hlavičce byly vytvořeny vzhledem k nejistému pořadí, ve kterém se jednotky překladu účastní statické konstrukce. Chcete-li použít tyto objekty v takovém kontextu, musíte nejprve vytvořit objekt třídy [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objekty globálního datového proudu

|||
|-|-|
|[cerr](#cerr)|Určuje `cerr` globální datový proud.|
|[Cin](#cin)|Určuje `cin` globální datový proud.|
|[Ucpat](#clog)|Určuje `clog` globální datový proud.|
|[cout](#cout)|Určuje `cout` globální datový proud.|
|[wcerr řekl:](#wcerr)|Určuje `wcerr` globální datový proud.|
|[wcin](#wcin)|Určuje `wcin` globální datový proud.|
|[wclog](#wclog)|Určuje `wclog` globální datový proud.|
|[wcout](#wcout)|Určuje `wcout` globální datový proud.|

### <a name="cerr"></a><a name="cerr"></a>cerr

Objekt `cerr` řídí výstup do vyrovnávací paměti `stderr`datového \<proudu přidružené k objektu , deklarované v cstdio>.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream.](../standard-library/ostream-typedefs.md#ostream)

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení bez vyrovnávací paměti do standardního výstupu chyb jako bajtový datový proud. Jakmile je objekt vytvořen, `cerr.`výraz [příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) je `cerr.tie() == &cout`nenulová a .

#### <a name="example"></a>Příklad

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a>Cin

Určuje `cin` globální datový proud.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [istream.](../standard-library/istream-typedefs.md#istream)

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako bajtový proud. Jakmile je objekt vytvořen, `cin.`volání `&` [tie](../standard-library/basic-ios-class.md#tie) vrátí [cout](#cout).

#### <a name="example"></a>Příklad

V tomto `cin` příkladu nastaví bit selhání v datovém proudu, když narazíte na nečíselné znaky. Program vymaže bit selhání a odstraní neplatný znak z datového proudu pokračovat.

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a>Ucpat

Určuje `clog` globální datový proud.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream.](../standard-library/ostream-typedefs.md#ostream)

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení do vyrovnávací paměti do standardního výstupu chyb y jako bajtový datový proud.

#### <a name="example"></a>Příklad

Příklad použití `clog`naleznete [v tématu](#cerr) .

### <a name="cout"></a><a name="cout"></a>cout

Určuje `cout` globální datový proud.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream.](../standard-library/ostream-typedefs.md#ostream)

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení do standardního výstupu jako bajtový proud.

#### <a name="example"></a>Příklad

Příklad použití `cout`naleznete [v tématu](#cerr) .

### <a name="wcerr"></a><a name="wcerr"></a>wcerr řekl:

Určuje `wcerr` globální datový proud.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream.](../standard-library/ostream-typedefs.md#wostream)

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení bez vyrovnávací paměti do standardního výstupu chyb jako široký datový proud. Jakmile je objekt vytvořen, `wcerr.`výraz [příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) je nenulová.

#### <a name="example"></a>Příklad

Příklad použití `wcerr`naleznete [v tématu](#cerr) .

### <a name="wcin"></a><a name="wcin"></a>wcin

Určuje `wcin` globální datový proud.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wistreamu.](../standard-library/istream-typedefs.md#wistream)

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako široký datový proud. Jakmile je objekt vytvořen, `wcin.`volání `&` [tie](../standard-library/basic-ios-class.md#tie) vrátí [wcout](#wcout).

#### <a name="example"></a>Příklad

Příklad použití `wcin`naleznete [v tématu](#cerr) .

### <a name="wclog"></a><a name="wclog"></a>wclog

Určuje `wclog` globální datový proud.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream.](../standard-library/ostream-typedefs.md#wostream)

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení do vyrovnávací paměti do standardního výstupu chyb jako široký datový proud.

#### <a name="example"></a>Příklad

Příklad použití `wclog`naleznete [v tématu](#cerr) .

### <a name="wcout"></a><a name="wcout"></a>wcout

Určuje `wcout` globální datový proud.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream.](../standard-library/ostream-typedefs.md#wostream)

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení do standardního výstupu jako široký datový proud.

#### <a name="example"></a>Příklad

Příklad použití `wcout`naleznete [v tématu](#cerr) .

`CString`instance v `wcout` příkazu musí `const wchar_t*`být přetypována na , jak je znázorněno v následujícím příkladu.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Další informace naleznete v [tématu Basic CString Operations](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
