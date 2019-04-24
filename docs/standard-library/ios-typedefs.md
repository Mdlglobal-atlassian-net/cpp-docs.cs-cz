---
title: '&lt;IOS&gt; – definice TypeDef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 1f0ff93c22263ca4b35377b5d9af089816e8895a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159259"
---
# <a name="ltiosgt-typedefs"></a>&lt;IOS&gt; – definice TypeDef

||||
|-|-|-|
|[IOS](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|

## <a name="ios"></a>  IOS

Podporuje ios třídy z původní Knihovna iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ios –](../standard-library/basic-ios-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="streamoff"></a>  streamoff

Podporuje vnitřní operace.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Poznámky

Typ je celé číslo se znaménkem, který popisuje objekt, který můžete uložit bajtovým posunem zahrnutých v různých stream umístění operace. Její reprezentace obsahuje alespoň 32 bitů hodnotu. Není nutně dostatečně velký pro reprezentaci libovolného bajtu v rámci datového proudu. Hodnota `streamoff(-1)` obvykle naznačuje chybný posun.

## <a name="streampos"></a>  streampos

Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatel na soubor.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [fpos –](../standard-library/fpos-class.md)< `mbstate_t`>.

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

## <a name="streamsize"></a>  streamsize

Označuje velikost datového proudu.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Poznámky

Typ je celé číslo se znaménkem, který popisuje objekt, který může ukládat počet prvků, které jsou zahrnuté v různých operací datového proudu. Její reprezentace obsahuje aspoň 16 bitů. Není nutně dostatečně velký pro reprezentaci libovolného bajtu v rámci datového proudu.

### <a name="example"></a>Příklad

Po zkompilování a spuštění následujícího programu, podívejte se na souboru test.txt a vidět její účinek nastavení `streamsize`.

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

## <a name="wios"></a>  wios

Podporuje wios třídy z původní Knihovna iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ios –](../standard-library/basic-ios-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="wstreampos"></a>  wstreampos

Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatel na soubor.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [fpos –](../standard-library/fpos-class.md)< `mbstate_t`>.

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

## <a name="see-also"></a>Viz také:

[\<ios>](../standard-library/ios.md)<br/>
