---
title: '&lt;fstream&gt; – definice TypeDef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 3fb38bcee6d23968e51e86fbde0b824cb7316ed4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; – definice TypeDef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Typ `basic_filebuf` specializované na `char` parametry šablony.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_filebuf](../standard-library/basic-filebuf-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="fstream"></a>  fstream

Typ `basic_fstream` specializované na `char` parametry šablony.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_fstream](../standard-library/basic-fstream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="ifstream"></a>  ifstream

Definuje proud, který se má použít ke čtení dat znakovou sériově ze souboru. `ifstream` je typedef, který se specializuje šablony třídy `basic_ifstream` pro `char`.

K dispozici je také `wifstream`, typedef, který se specializuje `basic_ifstream` číst `wchar_t` dvojité šířce znaků. Další informace najdete v tématu [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ifstream](../standard-library/basic-ifstream-class.md), specializované pro elementy znakový typ s vlastnostmi výchozí znak. Příkladem je

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

Typ `basic_ofstream` specializované na `char` parametry šablony.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ofstream](../standard-library/basic-ofstream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.

## <a name="wfstream"></a>  wfstream

Typ `basic_fstream` specializované na `wchar_t` parametry šablony.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_fstream](../standard-library/basic-fstream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="wifstream"></a>  wifstream

Typ `basic_ifstream` specializované na `wchar_t` parametry šablony.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ifstream](../standard-library/basic-ifstream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="wofstream"></a>  wofstream

Typ `basic_ofstream` specializované na `wchar_t` parametry šablony.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ofstream](../standard-library/basic-ofstream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="wfilebuf"></a>  wfilebuf

Typ `basic_filebuf` specializované na `wchar_t` parametry šablony.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_filebuf](../standard-library/basic-filebuf-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.

## <a name="see-also"></a>Viz také

[\<fstream >](../standard-library/fstream.md)<br/>
