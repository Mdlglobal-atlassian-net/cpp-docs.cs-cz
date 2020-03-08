---
title: '&lt;fstream –&gt; definice typedef'
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
ms.openlocfilehash: 3f4104b28f5becfdbf62ede16faa81e855fcac8c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876110"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream –&gt; definice typedef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream –](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>filebuf

Typ `basic_filebuf` specializované na parametrech **char** Template.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="fstream"></a>fstream –

Typ `basic_fstream` specializované na parametrech **char** Template.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_fstream](../standard-library/basic-fstream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="ifstream"></a>ifstream

Definuje datový proud, který se má použít ke čtení jednobajtových znakových dat ze souboru sériově. `ifstream` je definice typu, která se specializuje `basic_ifstream` šablony třídy pro **char**.

K dispozici je také `wifstream`definice typedef, která se specializuje `basic_ifstream` na čtení **wchar_t** dvojitě velkých znaků. Další informace najdete v tématu [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ifstream](../standard-library/basic-ifstream-class.md)specializované pro prvky typu char s výchozími vlastnostmi znaků. Příkladem je

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>ofstream

Typ `basic_ofstream` specializované na parametrech **char** Template.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ofstream](../standard-library/basic-ofstream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wfstream"></a>wfstream

Typ `basic_fstream` specializované na **wchar_t** parametrů šablony.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_fstream](../standard-library/basic-fstream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wifstream"></a>wifstream

Typ `basic_ifstream` specializované na **wchar_t** parametrů šablony.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ifstream](../standard-library/basic-ifstream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wofstream"></a>wofstream

Typ `basic_ofstream` specializované na **wchar_t** parametrů šablony.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ofstream](../standard-library/basic-ofstream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wfilebuf"></a>wfilebuf

Typ `basic_filebuf` specializované na **wchar_t** parametrů šablony.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také

[\<fstream – >](../standard-library/fstream.md)
