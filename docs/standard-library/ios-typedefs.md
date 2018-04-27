---
title: '&lt;IOS&gt; – definice TypeDef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
caps.latest.revision: 13
manager: ghogen
ms.openlocfilehash: 94b86b583e00507b89a1b087f3bb8817cf10de29
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltiosgt-typedefs"></a>&lt;IOS&gt; – definice TypeDef

||||
|-|-|-|
|[IOS](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|

## <a name="ios"></a>  IOS

Podporuje ios třída ze staré knihovny iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ios](../standard-library/basic-ios-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="streamoff"></a>  streamoff

Podporuje interní operace.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Poznámky

Typ se znaménkem popisující objekt, který může ukládat posun bajtů, která je zahrnutých v různých datového proudu umístění operace. Její reprezentace má alespoň 32 bity hodnotu. Není nezbytně dostatečně velký pro představují libovolné bajtů pozici v rámci datového proudu. Hodnota **streamoff(-1)** obvykle označuje chybné posun.

## <a name="streampos"></a>  streampos

Obsahuje aktuální pozici vyrovnávací paměti ukazatele nebo ukazatele souboru.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

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

Typ se znaménkem, který popisuje objekt, který může ukládat počet elementů účastnících se operace s různými datovými proudy. Její reprezentace má alespoň 16 bitů. Není nezbytně dostatečně velký pro představují libovolné bajtů pozici v rámci datového proudu.

### <a name="example"></a>Příklad

Po kompilaci a spuštění následujícího programu, podívejte se na soubor test.txt zobrazíte účinek nastavení `streamsize`.

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

Podporuje třídě wios ze staré knihovny iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ios](../standard-library/basic-ios-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="wstreampos"></a>  wstreampos

Obsahuje aktuální pozici vyrovnávací paměti ukazatele nebo ukazatele souboru.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

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

## <a name="see-also"></a>Viz také

[\<IOS >](../standard-library/ios.md)<br/>
