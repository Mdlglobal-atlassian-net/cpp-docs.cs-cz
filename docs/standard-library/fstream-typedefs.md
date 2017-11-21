---
title: "&lt;fstream&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 55a148c472048c5531521cd6f4574477e7c31cac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; – definice TypeDef
||||  
|-|-|-|  
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|  
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|  
|[wifstream](#wifstream)|[wofstream](#wofstream)|  
  
##  <a name="filebuf"></a>filebuf  
 Typ `basic_filebuf` specializované na `char` parametry šablony.  
  
```
typedef basic_filebuf<char, char_traits<char>> filebuf;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_filebuf](../standard-library/basic-filebuf-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="fstream"></a>fstream  
 Typ `basic_fstream` specializované na `char` parametry šablony.  
  
```
typedef basic_fstream<char, char_traits<char>> fstream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_fstream](../standard-library/basic-fstream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="ifstream"></a>ifstream  
 Definuje proud, který se má použít ke čtení dat znakovou sériově ze souboru. `ifstream`je typedef, který se specializuje šablony třídy `basic_ifstream` pro `char`.  
  
 K dispozici je také `wifstream`, typedef, který se specializuje `basic_ifstream` číst `wchar_t` dvojité šířce znaků. Další informace najdete v tématu [wifstream](../standard-library/fstream-typedefs.md#wifstream).  
  
```
typedef basic_ifstream<char, char_traits<char>> ifstream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony `basic_ifstream`, specializované pro elementy znakový typ s vlastnostmi výchozí znak. Příkladem je  
  
 `using namespace std;`  
  
 `ifstream infile("existingtextfile.txt");`  
  
 `if (!infile.bad())`  
  
 `{`  
  
 `// Dump the contents of the file to cout.`  
  
 `cout << infile.rdbuf();`  
  
 `infile.close();`  
  
 `}`  
  
##  <a name="ofstream"></a>ofstream  
 Typ `basic_ofstream` specializované na `char` parametry šablony.  
  
```
typedef basic_ofstream<char, char_traits<char>> ofstream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_ofstream](../standard-library/basic-ofstream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="wfstream"></a>wfstream  
 Typ `basic_fstream` specializované na `wchar_t` parametry šablony.  
  
```
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_fstream](../standard-library/basic-fstream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
##  <a name="wifstream"></a>wifstream  
 Typ `basic_ifstream` specializované na `wchar_t` parametry šablony.  
  
```
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_ifstream](../standard-library/basic-ifstream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
##  <a name="wofstream"></a>wofstream  
 Typ `basic_ofstream` specializované na `wchar_t` parametry šablony.  
  
```
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_ofstream](../standard-library/basic-ofstream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
##  <a name="wfilebuf"></a>wfilebuf  
 Typ `basic_filebuf` specializované na `wchar_t` parametry šablony.  
  
```
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_filebuf](../standard-library/basic-filebuf-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
## <a name="see-also"></a>Viz také  
 [\<fstream >](../standard-library/fstream.md)



