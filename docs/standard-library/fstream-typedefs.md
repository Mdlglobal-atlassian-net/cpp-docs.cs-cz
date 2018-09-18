---
title: '&lt;fstream –&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: dcae38b92d4740758bad00bc6e07555654dfd973
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018051"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream –&gt; – definice TypeDef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream –](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Typ `basic_filebuf` specializované na **char** parametry šablony.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="fstream"></a>  fstream –

Typ `basic_fstream` specializované na **char** parametry šablony.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_fstream –](../standard-library/basic-fstream-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="ifstream"></a>  ifstream

Definuje datový proud, který se má použít ke čtení dat jednobajtový znak sériově ze souboru. `ifstream` Definice TypeDef, která se specializuje na třídu šablony `basic_ifstream` pro **char**.

K dispozici je také `wifstream`, definice typedef, která se specializuje na `basic_ifstream` číst **wchar_t** dvojnásobně široké znaky. Další informace najdete v tématu [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ifstream –](../standard-library/basic-ifstream-class.md)specializované pro prvky typu char s výchozí vlastností. Příkladem je

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

Typ `basic_ofstream` specializované na **char** parametry šablony.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ofstream –](../standard-library/basic-ofstream-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="wfstream"></a>  wfstream

Typ `basic_fstream` specializované na **wchar_t** parametry šablony.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_fstream –](../standard-library/basic-fstream-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="wifstream"></a>  wifstream

Typ `basic_ifstream` specializované na **wchar_t** parametry šablony.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ifstream –](../standard-library/basic-ifstream-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="wofstream"></a>  wofstream

Typ `basic_ofstream` specializované na **wchar_t** parametry šablony.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ofstream –](../standard-library/basic-ofstream-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="wfilebuf"></a>  wfilebuf

Typ `basic_filebuf` specializované na **wchar_t** parametry šablony.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="see-also"></a>Viz také:

[\<fstream – >](../standard-library/fstream.md)<br/>
