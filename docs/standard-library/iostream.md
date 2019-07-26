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
ms.openlocfilehash: 471b149eba32d163e6e3e54e1c2820bbe0b94133
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449044"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje objekty, které řídí čtení z a zápis na standardní datové proudy. Toto zahrnutí je často jedinou hlavičkou, kterou potřebujete ke vstupu a výstupu z C++ programu.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

> [!NOTE]
> `#include <streambuf>` `#include <istream>`Knihovna > `#include <ios>`iostream–používápříkazy,, a`#include <ostream>` . \<

## <a name="remarks"></a>Poznámky

Objekty spadají do dvou skupin:

- [CIN](#cin), [cout](#cout), [cerr](#cerr)a [CLOG](#clog) jsou orientované na bajt, což vede k konvenčním přenosům v bajtech.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr)a [wclog](#wclog) jsou orientované na rozsáhlou škálu, překládá se na a ze znaků, které program zpracovává interně.

Jakmile provedete určité operace s datovým proudem, jako je například standardní vstup, nemůžete provádět operace s jinou orientací na stejném datovém proudu. Proto program nemůže pracovat zaměnitelné na [CIN](#cin) i [wcin](#wcin), například.

Všechny objekty deklarované v této hlavičce sdílejí zvláštní vlastnost – můžete předpokládat, že jsou vytvořeny před všemi definovanými statickými objekty, v jednotce překladu, která zahrnuje \<iostream – >. Stejně tak můžete předpokládat, že tyto objekty nejsou zničeny před destruktory pro jakékoli takové statické objekty, které definujete. (Výstupní proudy se ale při ukončení programu vyprázdní.) Z tohoto důvodu můžete bezpečně číst nebo zapisovat na standardní proudy před spuštěním programu a po ukončení programu.

Tato záruka ale není univerzální. Statický konstruktor může volat funkci v jiné jednotce překladu. Volaná funkce nemůže předpokládat, že objekty deklarované v této hlavičce byly sestaveny, vzhledem k neurčitému pořadí, ve kterém se jednotky překladu účastní statické konstrukce. Chcete-li použít tyto objekty v takovém kontextu, je nutné nejprve vytvořit objekt třídy [ios_base:: init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objekty globálního streamu

|||
|-|-|
|[cerr](#cerr)|`cerr` Určuje globální datový proud.|
|[cin](#cin)|`cin` Určuje globální datový proud.|
|[clog](#clog)|`clog` Určuje globální datový proud.|
|[cout](#cout)|`cout` Určuje globální datový proud.|
|[wcerr](#wcerr)|`wcerr` Určuje globální datový proud.|
|[wcin](#wcin)|`wcin` Určuje globální datový proud.|
|[wclog](#wclog)|`wclog` Určuje globální datový proud.|
|[wcout](#wcout)|`wcout` Určuje globální datový proud.|

###  <a name="cerr"></a>cerr

Objekt `cerr` řídí výstup do vyrovnávací paměti datového proudu přidružené k objektu `stderr`deklarovanému v \<cstdio >.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do vyrovnávací paměti do standardního výstupu chyb jako datový proud bajtů. Po sestavení `cerr.`objektu jsou [příznaky](../standard-library/ios-base-class.md#flags) `&` výrazu [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulové a `cerr.tie() == &cout`.

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

###  <a name="cin"></a>cin

`cin` Určuje globální datový proud.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [IStream](../standard-library/istream-typedefs.md#istream) .

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako datový proud bajtů. Jakmile je objekt vytvořen, `cin.`funkce Call [spojí](../standard-library/basic-ios-class.md#tie) vrátí `&` [cout](#cout).

#### <a name="example"></a>Příklad

V tomto příkladu `cin` nastaví bit selhání v datovém proudu, pokud je k dispozici přes jiné než číselné znaky. Program vymaže bit selhání a odstraní neplatný znak z datového proudu, aby bylo možné pokračovat.

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

###  <a name="clog"></a>clog

`clog` Určuje globální datový proud.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do vyrovnávací paměti do standardního výstupu chyby jako datový proud bajtů.

#### <a name="example"></a>Příklad

Příklad [](#cerr) použití `clog`naleznete v tématu cerr.

###  <a name="cout"></a>cout

`cout` Určuje globální datový proud.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládací prvky vloží do standardního výstupu jako datový proud bajtů.

#### <a name="example"></a>Příklad

Příklad [](#cerr) použití `cout`naleznete v tématu cerr.

### <a name="wcerr"></a>wcerr

`wcerr` Určuje globální datový proud.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream –](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do standardního výstupu chyb jako datový proud, který není uložen do vyrovnávací paměti. Po sestavení objektu jsou `wcerr.` [příznaky](../standard-library/ios-base-class.md#flags) `&` výrazu [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulové.

#### <a name="example"></a>Příklad

Příklad [](#cerr) použití `wcerr`naleznete v tématu cerr.

### <a name="wcin"></a>wcin

`wcin` Určuje globální datový proud.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wistream](../standard-library/istream-typedefs.md#wistream) .

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako datový proud. Jakmile je objekt vytvořen, `wcin.`funkce Call [spojí](../standard-library/basic-ios-class.md#tie) vrátí `&` [wcout](#wcout).

#### <a name="example"></a>Příklad

Příklad [](#cerr) použití `wcin`naleznete v tématu cerr.

### <a name="wclog"></a>wclog

`wclog` Určuje globální datový proud.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream –](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do vyrovnávací paměti standardního výstupu jako velký datový proud.

#### <a name="example"></a>Příklad

Příklad [](#cerr) použití `wclog`naleznete v tématu cerr.

### <a name="wcout"></a>wcout

`wcout` Určuje globální datový proud.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream –](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládací prvky vloží do standardního výstupu jako velký datový proud.

#### <a name="example"></a>Příklad

Příklad [](#cerr) použití `wcout`naleznete v tématu cerr.

`CString`instance v `wcout` příkazu musí být přetypování do `const wchar_t*`, jak je znázorněno v následujícím příkladu.

```
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Další informace najdete v tématu [základní operace CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
