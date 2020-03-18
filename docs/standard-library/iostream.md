---
title: '&lt;iostream –&gt;'
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
ms.openlocfilehash: 2906e802072c43a93c59ca40d15e032adeeeef97
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418914"
---
# <a name="ltiostreamgt"></a>&lt;iostream –&gt;

Deklaruje objekty, které řídí čtení z a zápis na standardní datové proudy. Toto zahrnutí je často jedinou hlavičkou, kterou potřebujete ke vstupu a výstupu z C++ programu.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

> [!NOTE]
> Knihovna > \<iostream – používá příkazy `#include <ios>`, `#include <streambuf>`, `#include <istream>`a `#include <ostream>`.

## <a name="remarks"></a>Poznámky

Objekty spadají do dvou skupin:

- [CIN](#cin), [cout](#cout), [cerr](#cerr)a [CLOG](#clog) jsou orientované na bajt, což vede k konvenčním přenosům v bajtech.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr)a [wclog](#wclog) jsou orientované na rozsáhlou škálu, překládá se na a ze znaků, které program zpracovává interně.

Jakmile provedete určité operace s datovým proudem, jako je například standardní vstup, nemůžete provádět operace s jinou orientací na stejném datovém proudu. Proto program nemůže pracovat zaměnitelné na [CIN](#cin) i [wcin](#wcin), například.

Všechny objekty deklarované v této hlavičce sdílejí zvláštní vlastnost – můžete předpokládat, že jsou vytvořené před všemi definovanými statickými objekty, v jednotce překladu, která obsahuje \<> iostream –. Stejně tak můžete předpokládat, že tyto objekty nejsou zničeny před destruktory pro jakékoli takové statické objekty, které definujete. (Výstupní proudy se ale při ukončení programu vyprázdní.) Z tohoto důvodu můžete bezpečně číst nebo zapisovat na standardní proudy před spuštěním programu a po ukončení programu.

Tato záruka ale není univerzální. Statický konstruktor může volat funkci v jiné jednotce překladu. Volaná funkce nemůže předpokládat, že objekty deklarované v této hlavičce byly sestaveny, vzhledem k neurčitému pořadí, ve kterém se jednotky překladu účastní statické konstrukce. Chcete-li použít tyto objekty v takovém kontextu, je nutné nejprve vytvořit objekt třídy [ios_base:: init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objekty globálního streamu

|||
|-|-|
|[cerr](#cerr)|Určuje `cerr` globální datový proud.|
|[cin](#cin)|Určuje `cin` globální datový proud.|
|[clog](#clog)|Určuje `clog` globální datový proud.|
|[cout](#cout)|Určuje `cout` globální datový proud.|
|[wcerr](#wcerr)|Určuje `wcerr` globální datový proud.|
|[wcin](#wcin)|Určuje `wcin` globální datový proud.|
|[wclog](#wclog)|Určuje `wclog` globální datový proud.|
|[wcout](#wcout)|Určuje `wcout` globální datový proud.|

###  <a name="cerr"></a>cerr

Objekt `cerr` řídí výstup do vyrovnávací paměti datového proudu přidružené k objektu `stderr`deklarované v \<cstdio >.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do vyrovnávací paměti do standardního výstupu chyb jako datový proud bajtů. Jakmile je objekt vytvořen, výraz `cerr.`[příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) je nenulový a `cerr.tie() == &cout`.

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

Určuje `cin` globální datový proud.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [IStream](../standard-library/istream-typedefs.md#istream) .

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako datový proud bajtů. Jakmile je objekt vytvořen, [volání `cin.`propojení](../standard-library/basic-ios-class.md#tie) vrátí `&`[cout](#cout).

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

Určuje `clog` globální datový proud.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do vyrovnávací paměti do standardního výstupu chyby jako datový proud bajtů.

#### <a name="example"></a>Příklad

Příklad použití `clog`naleznete v tématu [cerr](#cerr) .

###  <a name="cout"></a>cout

Určuje `cout` globální datový proud.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládací prvky vloží do standardního výstupu jako datový proud bajtů.

#### <a name="example"></a>Příklad

Příklad použití `cout`naleznete v tématu [cerr](#cerr) .

### <a name="wcerr"></a>wcerr

Určuje `wcerr` globální datový proud.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream –](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do standardního výstupu chyb jako datový proud, který není uložen do vyrovnávací paměti. Jakmile je objekt vytvořen, výraz `wcerr.`[příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) je nenulový.

#### <a name="example"></a>Příklad

Příklad použití `wcerr`naleznete v tématu [cerr](#cerr) .

### <a name="wcin"></a>wcin

Určuje `wcin` globální datový proud.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wistream](../standard-library/istream-typedefs.md#wistream) .

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako datový proud. Jakmile je objekt vytvořen, [volání `wcin.`propojení](../standard-library/basic-ios-class.md#tie) vrátí `&`[wcout](#wcout).

#### <a name="example"></a>Příklad

Příklad použití `wcin`naleznete v tématu [cerr](#cerr) .

### <a name="wclog"></a>wclog

Určuje `wclog` globální datový proud.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream –](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládá vložená vložení do vyrovnávací paměti standardního výstupu jako velký datový proud.

#### <a name="example"></a>Příklad

Příklad použití `wclog`naleznete v tématu [cerr](#cerr) .

### <a name="wcout"></a>wcout

Určuje `wcout` globální datový proud.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt [wostream –](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Poznámky

Objekt ovládací prvky vloží do standardního výstupu jako velký datový proud.

#### <a name="example"></a>Příklad

Příklad použití `wcout`naleznete v tématu [cerr](#cerr) .

instance `CString` v příkazu `wcout` musí být přetypování na `const wchar_t*`, jak je znázorněno v následujícím příkladu.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Další informace najdete v tématu [základní operace CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Viz také

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream – programování](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
