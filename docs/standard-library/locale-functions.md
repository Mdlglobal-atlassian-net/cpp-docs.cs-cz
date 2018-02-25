---
title: "&lt;národní prostředí&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 8f038a52d996fb33564e073b07beba501cc053cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltlocalegt-functions"></a>&lt;národní prostředí&gt; funkce
||||  
|-|-|-|  
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|  
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|  
|[islower](#islower)|[isprint](#isprint)|[ispunct –](#ispunct)|  
|[isspace](#isspace)|[isupper –](#isupper)|[isxdigit](#isxdigit)|  
|[ToLower](#tolower)|[ToUpper](#toupper)|[use_facet](#use_facet)|  
  
##  <a name="has_facet"></a>  has_facet  
 Ověřuje, zda je v zadaném národním prostředí uložena konkrétní omezující vlastnost.  
  
```  
template <class Facet>  
bool has_facet(const locale& Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `Loc`  
 Národní prostředí má být testována přítomnost omezující vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud národní prostředí má omezující vlastnost testována; **false** Pokud neexistuje.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony je užitečné pro kontrolu, jestli nonmandatory omezující vlastnosti jsou uvedeny v národním prostředí před `use_facet` je volána, aby se zabránilo výjimku, která by být vyvolána, pokud nebyly nalezeny.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_has_facet.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   locale loc ( "German_Germany" );  
   bool result = has_facet <ctype<char> > ( loc );  
   cout << result << endl;  
}  
```  
  
```Output  
1  
```  
  
##  <a name="isalnum"></a>  isalnum –  
 Ověřuje, zda je prvek v národním prostředí abecední, nebo číselný znak.  
  
```  
template <class CharType>  
bool isalnum(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Alfanumerické element, který má být testována.  
  
 `Loc`  
 Národní prostředí obsahující alfanumerické element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována alfanumerické; **false** Pokud není.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_isalnum.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isalnum ( 'L', loc);  
   bool result2 = isalnum ( '@', loc);  
   bool result3 = isalnum ( '3', loc);  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "alphanumeric." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not alphanumeric." << endl;  
  
   if ( result2 )  
      cout << "The character '@' in the locale is "  
           << "alphanumeric." << endl;  
   else  
      cout << "The character '@' in the locale is "  
           << " not alphanumeric." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "alphanumeric." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not alphanumeric." << endl;  
}  
```  
  
```Output  
The character 'L' in the locale is alphanumeric.  
The character '@' in the locale is  not alphanumeric.  
The character '3' in the locale is alphanumeric.  
```  
  
##  <a name="isalpha"></a>  isalpha –  
 Ověřuje, zda se jedná o prvek v národního prostředí je znak abecedy.  
  
```  
template <class CharType>  
bool isalpha(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí obsahující abecední znaky element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována abecedním; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **alpha**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_isalpha.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isalpha ( 'L', loc);  
   bool result2 = isalpha ( '@', loc);  
   bool result3 = isalpha ( '3', loc);  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "alphabetic." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not alphabetic." << endl;  
  
   if ( result2 )  
      cout << "The character '@' in the locale is "  
           << "alphabetic." << endl;  
   else  
      cout << "The character '@' in the locale is "  
           << " not alphabetic." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "alphabetic." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not alphabetic." << endl;  
}  
```  
  
##  <a name="iscntrl"></a>  iscntrl –  
 Ověřuje, zda je prvek v národním prostředí řídicí znak.  
  
```  
template <class CharType>  
bool iscntrl(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována řídicí znak; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **stisknutím kláves CTRL +**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_iscntrl.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = iscntrl ( 'L', loc );  
   bool result2 = iscntrl ( '\n', loc );  
   bool result3 = iscntrl ( '\t', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a control character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a control character." << endl;  
  
   if ( result2 )  
      cout << "The character-set 'backslash-n' in the locale\n is "  
           << "a control character." << endl;  
   else  
      cout << "The character-set 'backslash-n' in the locale\n is "  
           << " not a control character." << endl;  
  
   if ( result3 )  
      cout << "The character-set 'backslash-t' in the locale\n is "  
           << "a control character." << endl;  
   else  
      cout << "The character-set 'backslash-n' in the locale \n is "  
           << " not a control character." << endl;  
}  
```  
  
##  <a name="isdigit"></a>  IsDigit –  
 Ověřuje, zda je prvek v národním prostředí číselný znak.  
  
```  
template <class CharType>  
bool isdigit(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována číselné znak; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **číslice**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_is_digit.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isdigit ( 'L', loc );  
   bool result2 = isdigit ( '@', loc );  
   bool result3 = isdigit ( '3', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a numeric character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a numeric character." << endl;  
  
   if ( result2 )  
      cout << "The character '@' in the locale is "  
           << "a numeric character." << endl;  
   else  
      cout << "The character '@' in the locale is "  
           << " not a numeric character." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "a numeric character." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not a numeric character." << endl;  
}  
```  
  
##  <a name="isgraph"></a>  isgraph –  
 Ověřuje, zda je prvek v národním prostředí alfanumerický znak nebo znak interpunkce.  
  
```  
template <class CharType>  
bool isgraph(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testovány alfanumerické nebo interpunkční znaménko; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **grafu**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_is_graph.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   locale loc ( "German_Germany" );  
   bool result1 = isgraph ( 'L', loc );  
   bool result2 = isgraph ( '\t', loc );  
   bool result3 = isgraph ( '.', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is\n "  
           << "an alphanumeric or punctuation character." << endl;  
   else  
      cout << "The character 'L' in the locale is\n "  
           << " not an alphanumeric or punctuation character." << endl;  
  
   if ( result2 )  
      cout << "The character 'backslash-t' in the locale is\n "  
           << "an alphanumeric or punctuation character." << endl;  
   else  
      cout << "The character 'backslash-t' in the locale is\n "  
           << "not an alphanumeric or punctuation character." << endl;  
  
   if ( result3 )  
      cout << "The character '.' in the locale is\n "  
           << "an alphanumeric or punctuation character." << endl;  
   else  
      cout << "The character '.' in the locale is\n "  
           << " not an alphanumeric or punctuation character." << endl;  
}  
```  
  
##  <a name="islower"></a>  islower –  
 Ověřuje, zda je prvek v národním prostředí malé písmeno.  
  
```  
template <class CharType>  
bool islower(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována malé písmeno; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **nižší**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_islower.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = islower ( 'L', loc );  
   bool result2 = islower ( 'n', loc );  
   bool result3 = islower ( '3', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a lowercase character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a lowercase character." << endl;  
  
   if ( result2 )  
      cout << "The character 'n' in the locale is "  
           << "a lowercase character." << endl;  
   else  
      cout << "The character 'n' in the locale is "  
           << " not a lowercase character." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "a lowercase character." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not a lowercase character." << endl;  
}  
```  
  
##  <a name="isprint"></a>  isprint –  
 Ověřuje, zda je prvek v národním prostředí znak, který lze vytisknout.  
  
```  
template <class CharType>  
bool isprint(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována tisknutelná; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **tisku**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_isprint.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
  
   bool result1 = isprint ( 'L', loc );  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a printable character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a printable character." << endl;  
  
   bool result2 = isprint( '\t', loc );  
   if ( result2 )  
      cout << "The character 'backslash-t' in the locale is "  
           << "a printable character." << endl;  
   else  
      cout << "The character 'backslash-t' in the locale is "  
           << " not a printable character." << endl;  
  
   bool result3 = isprint( '\n', loc );  
   if ( result3 )  
      cout << "The character 'backslash-n' in the locale is "  
           << "a printable character." << endl;  
   else  
      cout << "The character 'backslash-n' in the locale is "  
           << " not a printable character." << endl;  
}  
```  
  
##  <a name="ispunct">ispunct –</a>  
 Ověřuje, zda je prvek v národním prostředí znak interpunkce.  
  
```  
template <class CharType>  
bool ispunct(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována interpunkční znaménko; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **punct**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_ispunct.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = ispunct ( 'L', loc );  
   bool result2 = ispunct ( ';', loc );  
   bool result3 = ispunct ( '*', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a punctuation character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a punctuation character." << endl;  
  
   if ( result2 )  
      cout << "The character ';' in the locale is "  
           << "a punctuation character." << endl;  
   else  
      cout << "The character ';' in the locale is "  
           << " not a punctuation character." << endl;  
  
   if ( result3 )  
      cout << "The character '*' in the locale is "  
           << "a punctuation character." << endl;  
   else  
      cout << "The character '*' in the locale is "  
           << " not a punctuation character." << endl;  
}  
```  
  
##  <a name="isspace"></a>  isspace –  
 Ověřuje, zda je prvek v národním prostředí prázdný znak.  
  
```  
template <class CharType>  
bool isspace(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testovány s prázdným znakem; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **místo**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_isspace.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isspace ( 'L', loc );  
   bool result2 = isspace ( '\n', loc );  
   bool result3 = isspace ( ' ', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a whitespace character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a whitespace character." << endl;  
  
   if ( result2 )  
      cout << "The character 'backslash-n' in the locale is "  
           << "a whitespace character." << endl;  
   else  
      cout << "The character 'backslash-n' in the locale is "  
           << " not a whitespace character." << endl;  
  
   if ( result3 )  
      cout << "The character ' ' in the locale is "  
           << "a whitespace character." << endl;  
   else  
      cout << "The character ' ' in the locale is "  
           << " not a whitespace character." << endl;  
}  
```  
  
##  <a name="isupper">isupper –</a>  
 Ověřuje, zda je element v národního prostředí velkými písmeny.  
  
```  
template <class CharType>  
bool isupper(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována velké písmeno; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **horní**, `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_isupper.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isupper ( 'L', loc );  
   bool result2 = isupper ( 'n', loc );  
   bool result3 = isupper ( '3', loc );  
  
   if ( result1 )  
      cout << "The character 'L' in the locale is "  
           << "a uppercase character." << endl;  
   else  
      cout << "The character 'L' in the locale is "  
           << " not a uppercase character." << endl;  
  
   if ( result2 )  
      cout << "The character 'n' in the locale is "  
           << "a uppercase character." << endl;  
   else  
      cout << "The character 'n' in the locale is "  
           << " not a uppercase character." << endl;  
  
   if ( result3 )  
      cout << "The character '3' in the locale is "  
           << "a uppercase character." << endl;  
   else  
      cout << "The character '3' in the locale is "  
           << " not a uppercase character." << endl;  
}  
```  
  
##  <a name="isxdigit"></a>  isxdigit –  
 Ověřuje, zda je prvek v národním prostředí znak používaný ke znázornění šestnáctkového čísla.  
  
```  
template <class CharType>  
bool isxdigit(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Element, který má být testována.  
  
 `Loc`  
 Národní prostředí, který obsahuje element, který má být testována.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je element testována znak se používá k reprezentování o hexadecimální číslo; **false** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **xdigit**, `Ch`).  
  
 Hexadecimální číslice využívá základní 16, který představuje čísla, pomocí čísla 0 až 9 plus písmena velká a malá písmena A až F představují desetinné číslice 0 až 15.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_isxdigit.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = isxdigit ( '5', loc );  
   bool result2 = isxdigit ( 'd', loc );  
   bool result3 = isxdigit ( 'q', loc );  
  
   if ( result1 )  
      cout << "The character '5' in the locale is "  
           << "a hexidecimal digit-character." << endl;  
   else  
      cout << "The character '5' in the locale is "  
           << " not a hexidecimal digit-character." << endl;  
  
   if ( result2 )  
      cout << "The character 'd' in the locale is "  
           << "a hexidecimal digit-character." << endl;  
   else  
      cout << "The character 'd' in the locale is "  
           << " not a hexidecimal digit-character." << endl;  
  
   if ( result3 )  
      cout << "The character 'q' in the locale is "  
           << "a hexidecimal digit-character." << endl;  
   else  
      cout << "The character 'q' in the locale is "  
           << " not a hexidecimal digit-character." << endl;  
}  
```  
  
##  <a name="tolower">ToLower</a>  
 Převede znak na malé písmeno.  
  
```  
template <class CharType>  
CharType tolower(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Znak, který má být převeden na malá písmena.  
  
 `Loc`  
 Národní prostředí, která obsahuje znak, který má být převeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Znak převeden na malá písmena.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [ToLower](../standard-library/ctype-class.md#tolower)( `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_tolower.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   char result1 = tolower ( 'H', loc );  
   cout << "The lower case of 'H' in the locale is: "  
        << result1 << "." << endl;  
   char result2 = tolower ( 'h', loc );  
   cout << "The lower case of 'h' in the locale is: "  
        << result2 << "." << endl;  
   char result3 = tolower ( '$', loc );  
   cout << "The lower case of '$' in the locale is: "  
        << result3 << "." << endl;  
}  
```  
  
##  <a name="toupper">ToUpper</a>  
 Převede znak na velké písmeno.  
  
```  
template <class CharType>  
CharType toupper(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Znak, který má být převeden na velká písmena.  
  
 `Loc`  
 Národní prostředí, která obsahuje znak, který má být převeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Znak převeden na velká písmena.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [ToUpper](../standard-library/ctype-class.md#toupper)( `Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_toupper.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   char result1 = toupper ( 'h', loc );  
   cout << "The upper case of 'h' in the locale is: "  
        << result1 << "." << endl;  
   char result2 = toupper ( 'H', loc );  
   cout << "The upper case of 'H' in the locale is: "  
        << result2 << "." << endl;  
   char result3 = toupper ( '$', loc );  
   cout << "The upper case of '$' in the locale is: "  
        << result3 << "." << endl;  
}  
```  
  
##  <a name="use_facet"></a>  use_facet  
 Vrátí odkaz na omezující vlastnost určitého typu uloženou v národním prostředí.  
  
```  
template <class Facet>  
const Facet& use_facet(const locale& Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `Loc`  
 Const národní prostředí obsahující typ omezující vlastnosti se na ně odkazovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na omezující vlastnost třídy `Facet` obsažené v argumentu národní prostředí.  
  
### <a name="remarks"></a>Poznámky  
 Odkaz na omezující vlastnost vrácené funkcí šablony zůstává platná, dokud všechny kopie obsahující národní prostředí existuje. Pokud žádný takový objekt omezující vlastnosti třídy `Facet` je uveden v národním prostředí argument, funkce vrátí `bad_cast` výjimka.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// locale_use_facet.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );  
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(  
   ctype_base::alpha, 'a'   
);  
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'  
   );  
  
   if ( result1 )  
      cout << "The character 'a' in locale loc1 is alphabetic."   
           << endl;  
   else  
      cout << "The character 'a' in locale loc1 is not alphabetic."   
           << endl;  
  
   if ( result2 )  
      cout << "The character '!' in locale loc2 is alphabetic."   
           << endl;  
   else  
      cout << "The character '!' in locale loc2 is not alphabetic."   
           << endl;  
}  
```  
  
```Output  
The character 'a' in locale loc1 is alphabetic.  
The character '!' in locale loc2 is not alphabetic.  
```  
  
## <a name="see-also"></a>Viz také  
 [\<národní prostředí >](../standard-library/locale.md)

