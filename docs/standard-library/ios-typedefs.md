---
title: '&lt;ios&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 0f63f65fb4c10fbe2ad538852222e6468b9061d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375403"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedefs

## <a name="ios"></a><a name="ios"></a>Ios

Podporuje třídu ios ze staré knihovny iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ios](../standard-library/basic-ios-class.md), specializované na prvky typu **char** s výchozí znakové znaky.

## <a name="streamoff"></a><a name="streamoff"></a>streamoff

Podporuje interní operace.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Poznámky

Typ je podepsané celé číslo, které popisuje objekt, který může uložit posun bajtu zapojený do různých operací umístění datového proudu. Jeho reprezentace má alespoň 32 bitů hodnoty. Není nutně dostatečně velký, aby představoval pozici libovolného bajtu v rámci datového proudu. Hodnota `streamoff(-1)` obecně označuje chybné posun.

## <a name="streampos"></a><a name="streampos"></a>streampos

Drží aktuální pozici ukazatele vyrovnávací paměti nebo ukazatele souboru.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Příklad

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a><a name="streamsize"></a>velikost datového proudu

Označuje velikost datového proudu.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Poznámky

Typ je podepsané celé číslo, které popisuje objekt, který může uložit počet prvků zapojených do různých operací datového proudu. Jeho reprezentace má alespoň 16 bitů. Není nutně dostatečně velký, aby představoval pozici libovolného bajtu v rámci datového proudu.

### <a name="example"></a>Příklad

Po kompilaci a spuštění následujícího programu se podívejte na soubor test.txt, abyste viděli vliv nastavení `streamsize`.

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## <a name="wios"></a><a name="wios"></a>wios

Podporuje třídu wios ze staré knihovny iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ios](../standard-library/basic-ios-class.md), specializované na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="wstreampos"></a><a name="wstreampos"></a>wstreampos

Drží aktuální pozici ukazatele vyrovnávací paměti nebo ukazatele souboru.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Příklad

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```
