---
title: '&lt;iOS&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 20bffbeb7720274302633c5dda9e6364c06d5b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856391"
---
# <a name="ltiosgt-typedefs"></a>&lt;iOS&gt; definice typedef

## <a name="ios"></a>iOS

Podporuje třídu iOS z staré knihovny iostream –.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ios](../standard-library/basic-ios-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="streamoff"></a>streamoff

Podporuje interní operace.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Poznámky

Typ je celé číslo se znaménkem, které popisuje objekt, který může ukládat posun bajtů v různých operacích umísťování datových proudů. Jeho reprezentace má minimálně 32 bitů hodnoty. Není dostatečně velká, aby představovala v datovém proudu libovolné místo v bajtech. Hodnota `streamoff(-1)` obecně označuje chybné posunutí.

## <a name="streampos"></a>streampos

Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatele na soubor.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

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

## <a name="streamsize"></a>StreamSize

Označuje velikost datového proudu.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Poznámky

Typ je celé číslo se znaménkem, které popisuje objekt, který může ukládat počet prvků, které jsou součástí různých operací streamování. Jeho reprezentace má alespoň 16 bitů. Není dostatečně velká, aby představovala v datovém proudu libovolné místo v bajtech.

### <a name="example"></a>Příklad

Po zkompilování a spuštění následujícího programu zkontrolujte soubor test. txt, abyste viděli účinek nastavení `streamsize`.

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

## <a name="wios"></a>wios

Podporuje třídu wios ze staré knihovny iostream –.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ios](../standard-library/basic-ios-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wstreampos"></a>wstreampos

Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatele na soubor.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

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
