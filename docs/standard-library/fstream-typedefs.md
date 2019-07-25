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
ms.openlocfilehash: 6144826254c6acc509db2c0285b21811fe37bd4e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454043"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream –&gt; definice typedef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream –](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>filebuf

Typ `basic_filebuf` specializovaný na parametry **znak** šablony.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_filebuf](../standard-library/basic-filebuf-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="fstream"></a>fstream –

Typ `basic_fstream` specializovaný na parametry **znak** šablony.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_fstream](../standard-library/basic-fstream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="ifstream"></a>ifstream

Definuje datový proud, který se má použít ke čtení jednobajtových znakových dat ze souboru sériově. `ifstream`je typedef, který se specializuje na třídu `basic_ifstream` šablony pro **char**.

K dispozici `wifstream`je také definice typedef, která `basic_ifstream` se specializuje na čtení dvojitě velkých znaků **wchar_t** . Další informace najdete v tématu [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ifstream](../standard-library/basic-ifstream-class.md)specializované pro prvky typu char s výchozími vlastnostmi znaků. Příkladem je

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

Typ `basic_ofstream` specializovaný na parametry **znak** šablony.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ofstream](../standard-library/basic-ofstream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wfstream"></a>wfstream

Typ `basic_fstream` specializovaný v parametrech šablony **wchar_t** .

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_fstream](../standard-library/basic-fstream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wifstream"></a>wifstream

Typ `basic_ifstream` specializovaný v parametrech šablony **wchar_t** .

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ifstream](../standard-library/basic-ifstream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wofstream"></a>wofstream

Typ `basic_ofstream` specializovaný v parametrech šablony **wchar_t** .

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ofstream](../standard-library/basic-ofstream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wfilebuf"></a>wfilebuf

Typ `basic_filebuf` specializovaný v parametrech šablony **wchar_t** .

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_filebuf](../standard-library/basic-filebuf-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také:

[\<fstream – >](../standard-library/fstream.md)
