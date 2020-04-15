---
title: '&lt;fstream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317184"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[filebuf (soubor)](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf řekl:](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>filebuf (soubor)

Typ `basic_filebuf` specializovaný na parametry šablony **char.**

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md), specializované na prvky typu **char** s výchozími znakovými znaky.

## <a name="fstream"></a><a name="fstream"></a>fstream

Typ `basic_fstream` specializovaný na parametry šablony **char.**

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_fstream](../standard-library/basic-fstream-class.md), specializované na prvky typu **char** s výchozími znakovými znaky.

## <a name="ifstream"></a><a name="ifstream"></a>ifstream

Definuje datový proud, který se má použít ke čtení jednobajtových znakových dat sériově ze souboru. `ifstream`je typedef, který se `basic_ifstream` specializuje na šablonu třídy pro **char**.

K dispozici `wifstream`je také , `basic_ifstream` typedef, který se specializuje na čtení **wchar_t** dvojité znaky. Další informace naleznete v tématu [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ifstream](../standard-library/basic-ifstream-class.md), specializované na prvky typu char s výchozími znakovými znaky. Příkladem je

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>ofstream

Typ `basic_ofstream` specializovaný na parametry šablony **char.**

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ofstream](../standard-library/basic-ofstream-class.md), specializované na prvky typu **char** s výchozími znakovými znaky.

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

Typ `basic_fstream` specializovaný na **parametry šablony wchar_t.**

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_fstream](../standard-library/basic-fstream-class.md), specializované na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="wifstream"></a><a name="wifstream"></a>wifstream

Typ `basic_ifstream` specializovaný na **parametry šablony wchar_t.**

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ifstream](../standard-library/basic-ifstream-class.md), specializované na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="wofstream"></a><a name="wofstream"></a>wofstream

Typ `basic_ofstream` specializovaný na **parametry šablony wchar_t.**

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ofstream](../standard-library/basic-ofstream-class.md), specializované na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf řekl:

Typ `basic_filebuf` specializovaný na **parametry šablony wchar_t.**

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md), specializované na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="see-also"></a>Viz také

[\<fstream>](../standard-library/fstream.md)
