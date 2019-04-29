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
ms.openlocfilehash: 18d6a8517d71cfa9c7e17a45c97f77977ec778f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385138"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje objekty, které určují čtení a zápis do standardních datových proudů. To je často jediným hlavičky, které je potřeba zahrnout provádět vstup a výstup z programu v jazyce C++.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

## <a name="remarks"></a>Poznámky

Objekty lze rozdělit do dvou skupin:

- [CIN](#cin), [cout](#cout), [cerr](#cerr), a [clog](#clog) jsou bajtů orientované na provádění konvenční přenosy bajtů v čase.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr), a [wclog](#wclog) orientovány široké, převod na a z široké znaky, které program pracuje interně.

Po provedení určitých operací v datovém proudu, jako je například standardní vstup nejde provést operace jinou orientaci pro stejný datový proud. Proto program nemůže pracovat Zaměnitelně obě [cin](#cin) a [wcin](#wcin), např.

Všechny objekty deklarované v této sdílené složce hlavičky specifické vlastnosti – jsou vytvořeny před všechny statické objekty definujete v jednotce překladu, který obsahuje, můžete předpokládat \<iostream – >. Stejnou měrou můžete předpokládat, že tyto objekty nejsou zničeny, před destruktory pro takové statických objektů, které definujete. (Výstupní datové proudy, ale vyprázdní při ukončení programu.) Proto může bezpečně číst nebo zapisovat do standardních streamů před spuštěním programu a po ukončení programu.

Tuto záruku však není univerzální. Statický konstruktor může volat funkci v jiné jednotce překladu. Volaná funkce nelze předpokládat, že objekty deklarované v této hlavičky mají byl vytvořen, daný neurčitém pořadí, ve které překlad jednotky účastnit statické konstrukce. Pokud chcete použít tyto objekty v této souvislosti, je nutné nejprve vytvořit objekt třídy [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Stream globální objekty

|||
|-|-|
|[cerr](#cerr)|Určuje, `cerr` globální datového proudu.|
|[cin](#cin)|Určuje, `cin` globální datového proudu.|
|[clog](#clog)|Určuje, `clog` globální datového proudu.|
|[cout](#cout)|Určuje, `cout` globální datového proudu.|
|[wcerr](#wcerr)|Určuje, `wcerr` globální datového proudu.|
|[wcin](#wcin)|Určuje, `wcin` globální datového proudu.|
|[wclog](#wclog)|Určuje, `wclog` globální datového proudu.|
|[wcout](#wcout)|Určuje, `wcout` globální datového proudu.|

###  <a name="cerr"></a>  cerr

Objekt `cerr` řídí výstup do vyrovnávací paměti datového proudu přidružená k objektu `stderr`, které jsou deklarovány v \<cstdio – >.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Návratová hodnota

[Ostream](../standard-library/ostream-typedefs.md#ostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt ovládacích prvků bez vyrovnávací paměti vložení do standardní chybový výstup jako datový proud bajtů. Po vytvoření objektu výraz `cerr.` [příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulové, a `cerr.tie() == &cout`.

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

###  <a name="cin"></a>  CIN

Určuje, `cin` globální datového proudu.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Návratová hodnota

[Istream](../standard-library/istream-typedefs.md#istream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt ovládacích prvků ze standardního vstupu extrakce jako datový proud bajtů. Po vytvoření objektu volání `cin.` [tie](../standard-library/basic-ios-class.md#tie) vrátí `&` [cout](#cout).

#### <a name="example"></a>Příklad

V tomto příkladu `cin` nastaví selhání bit v datovém proudu, pokud se setká s jiné než číselné znaky. Program vymaže bit selhání a odstraní neplatný znak z datového proudu, aby bylo možné pokračovat.

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

###  <a name="clog"></a>  clog

Určuje, `clog` globální datového proudu.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Návratová hodnota

[Ostream](../standard-library/ostream-typedefs.md#ostream) objektu.

#### <a name="remarks"></a>Poznámky

Ovládací prvky objektu ukládány do vyrovnávací paměti vložení do standardní chybový výstup jako datový proud bajtů.

#### <a name="example"></a>Příklad

Zobrazit [cerr](#cerr) pro příklad použití `clog`.

###  <a name="cout"></a>  cout

Určuje, `cout` globální datového proudu.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Návratová hodnota

[Ostream](../standard-library/ostream-typedefs.md#ostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení do standardního výstupního datového proudu bajtů.

#### <a name="example"></a>Příklad

Zobrazit [cerr](#cerr) pro příklad použití `cout`.

###  <a name="wcerr"></a>  wcerr

Určuje, `wcerr` globální datového proudu.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Návratová hodnota

A [wostream](../standard-library/ostream-typedefs.md#wostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt ovládacích prvků bez vyrovnávací paměti vložení do standardní chybový výstup jako široké datového proudu. Po vytvoření objektu výraz `wcerr.` [příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulové.

#### <a name="example"></a>Příklad

Zobrazit [cerr](#cerr) pro příklad použití `wcerr`.

###  <a name="wcin"></a>  wcin

Určuje, `wcin` globální datového proudu.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Návratová hodnota

A [wistream](../standard-library/istream-typedefs.md#wistream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt ovládacích prvků ze standardního vstupu extrakce jako široké datového proudu. Po vytvoření objektu volání `wcin.` [tie](../standard-library/basic-ios-class.md#tie) vrátí `&` [wcout](#wcout).

#### <a name="example"></a>Příklad

Zobrazit [cerr](#cerr) pro příklad použití `wcin`.

###  <a name="wclog"></a>  wclog

Určuje, `wclog` globální datového proudu.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Návratová hodnota

A [wostream](../standard-library/ostream-typedefs.md#wostream) objektu.

#### <a name="remarks"></a>Poznámky

Ovládací prvky objektu ukládány do vyrovnávací paměti vložení do standardní chybový výstup jako široké datový proud.

#### <a name="example"></a>Příklad

Zobrazit [cerr](#cerr) pro příklad použití `wclog`.

###  <a name="wcout"></a>  wcout

Určuje, `wcout` globální datového proudu.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Návratová hodnota

A [wostream](../standard-library/ostream-typedefs.md#wostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt určuje vložení do standardního výstupu jako široké datový proud.

#### <a name="example"></a>Příklad

Zobrazit [cerr](#cerr) pro příklad použití `wcout`.

`CString` instance `wcout` příkazu musí být přetypovat na `const wchar_t*`, jak je znázorněno v následujícím příkladu.

```

    CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;
```

Další informace najdete v tématu [základních operací CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
