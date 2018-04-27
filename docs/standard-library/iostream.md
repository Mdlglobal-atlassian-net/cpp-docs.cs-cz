---
title: '&lt;iostream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 09/20/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40b74dea33bbd4ed8436e8e90c35fb054974d0c7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje objekty, které řídí čtení a zápis do standardní datových proudů. Tento problém je často jenom hlavičky, kterou je nutné zahrnout provést vstup a výstup z programu C++.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>

```

## <a name="remarks"></a>Poznámky

Objekty lze rozdělit do dvou skupin:

- [CIN](#cin), [cout](#cout), [cerr](#cerr), a [clog](#clog) jsou bajtů zaměřené na konkrétní, provádění konvenční bajtů na čas přenosů.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr), a [wclog](#wclog) jsou celý orientované překladu do a z široké znaky, které program zpracovává interně.

Jakmile provádění některých operací na datový proud, jako je například standardní vstupní, nelze provádět operace jinou orientaci na stejného datového proudu. Proto program nemůže pracovat zcela zaměnitelným významem obě [cin](#cin) a [wcin](#wcin), např.

Všechny objekty v této sdílené složce záhlaví deklarována odborností společných vlastností – můžete předpokládat, jsou vytvořené před všechny statické objekty, které definujete v překlad jednotku, která obsahuje \<iostream >. Stejným způsobem můžete předpokládat, že nejsou tyto objekty zničen před destruktory pro tyto statické objekty, které definujete. (Výstupní datové proudy jsou, ale vyprázdněných při ukončení programu.) Proto může bezpečně číst nebo zapisovat do standardní datové proudy před spuštění programu a po ukončení programu.

Tato záruka není univerzální, ale. Statický konstruktor může volat funkci v jiné jednotce překlad. Volaná funkce nelze předpokládat, že s danou neurčitém pořadí, ve které překlad jednotky účastnit statické konstrukce mít byl vytvořený objekty deklarované v této hlavičce. V takové kontextu použít tyto objekty, je nutné nejprve vytvořit objekt třídy [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objekty globálních datových proudů

|||
|-|-|
|[cerr](#cerr)|Určuje, `cerr` globální datového proudu.|
|[CIN](#cin)|Určuje, `cin` globální datového proudu.|
|[clog](#clog)|Určuje, `clog` globální datového proudu.|
|[cout](#cout)|Určuje, `cout` globální datového proudu.|
|[wcerr](#wcerr)|Určuje, `wcerr` globální datového proudu.|
|[wcin](#wcin)|Určuje, `wcin` globální datového proudu.|
|[wclog](#wclog)|Určuje, `wclog` globální datového proudu.|
|[wcout](#wcout)|Určuje, `wcout` globální datového proudu.|

###  <a name="cerr"></a>  cerr

Objekt `cerr` řídí výstup do vyrovnávací paměti datový proud přidružený k objektu `stderr`, deklarované v \<cstdio – >.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Návratová hodnota

[Ostream –](../standard-library/ostream-typedefs.md#ostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí bez vyrovnávací paměti vložení standardní chyba výstupu pomocí datového proudu bajtů. Jakmile je objekt vytvořený, výraz `cerr.` [příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) je nenulové hodnoty, a `cerr.tie() == &cout`.

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

[IStream on Request](../standard-library/istream-typedefs.md#istream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako datový proud bajtů. Jakmile je objekt vytvořený, volání `cin.` [tie](../standard-library/basic-ios-class.md#tie) vrátí `&` [cout](#cout).

#### <a name="example"></a>Příklad

V tomto příkladu `cin` nastaví selhání bit v datovém proudu, pokud se setká s jiné než číselné znaky. Program vymaže bit služeb při selhání a odstraní neplatný znak z datového proudu, aby bylo možné pokračovat.

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

[Ostream –](../standard-library/ostream-typedefs.md#ostream) objektu.

#### <a name="remarks"></a>Poznámky

Ovládací prvky objektu do vyrovnávací paměti vložení standardní chyba výstupu pomocí datového proudu bajtů.

#### <a name="example"></a>Příklad

V tématu [cerr](#cerr) příklad použití `clog`.

###  <a name="cout"></a>  cout

Určuje, `cout` globální datového proudu.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Návratová hodnota

[Ostream –](../standard-library/ostream-typedefs.md#ostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení do standardního výstupního datového proudu bajtů.

#### <a name="example"></a>Příklad

V tématu [cerr](#cerr) příklad použití `cout`.

###  <a name="wcerr"></a>  wcerr

Určuje, `wcerr` globální datového proudu.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Návratová hodnota

A [wostream –](../standard-library/ostream-typedefs.md#wostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí bez vyrovnávací paměti vložení standardní chyba výstupu pomocí široké datového proudu. Jakmile je objekt vytvořený, výraz `wcerr.` [příznaky](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulový.

#### <a name="example"></a>Příklad

V tématu [cerr](#cerr) příklad použití `wcerr`.

###  <a name="wcin"></a>  wcin

Určuje, `wcin` globální datového proudu.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Návratová hodnota

A [wistream](../standard-library/istream-typedefs.md#wistream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí extrakce ze standardního vstupu jako široké datový proud. Jakmile je objekt vytvořený, volání `wcin.` [tie](../standard-library/basic-ios-class.md#tie) vrátí `&` [wcout](#wcout).

#### <a name="example"></a>Příklad

V tématu [cerr](#cerr) příklad použití `wcin`.

###  <a name="wclog"></a>  wclog

Určuje, `wclog` globální datového proudu.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Návratová hodnota

A [wostream –](../standard-library/ostream-typedefs.md#wostream) objektu.

#### <a name="remarks"></a>Poznámky

Ovládací prvky objektu do vyrovnávací paměti vložení do výstupu standardní chyba pomocí široké datového proudu.

#### <a name="example"></a>Příklad

V tématu [cerr](#cerr) příklad použití `wclog`.

###  <a name="wcout"></a>  wcout

Určuje, `wcout` globální datového proudu.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Návratová hodnota

A [wostream –](../standard-library/ostream-typedefs.md#wostream) objektu.

#### <a name="remarks"></a>Poznámky

Objekt řídí vložení ve standardním výstupu pomocí široké datového proudu.

#### <a name="example"></a>Příklad

V tématu [cerr](#cerr) příklad použití `wcout`.

`CString` instance v `wcout` musí být příkaz přetypovat `const wchar_t*`, jak je znázorněno v následujícím příkladu.

```

    CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;
```

Další informace najdete v tématu [základní operace CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
