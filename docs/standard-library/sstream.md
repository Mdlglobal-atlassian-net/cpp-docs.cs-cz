---
title: "&lt;sstream –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <sstream>
dev_langs: C++
helpviewer_keywords: sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04c6675dd7af1fbbd1202337dda2fcf3570f5be0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltsstreamgt"></a>&lt;sstream –&gt;
Definuje několik třídy šablony, které podporují operace iostreams v pořadí, které jsou uložené v objektu přidělené array. Takové pořadí se snadno převedou do a z objekty třídy šablony [basic_string](../standard-library/basic-string-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>  
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>  
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>  
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>  
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Odkaz na `sstream` objektu.|  
|`right`|Odkaz na `sstream` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Objekty typu `char *` můžete použít funkci v [ \<strstream – >](../standard-library/strstream.md) pro streamování. Ale `<strstream>` je zastaralý a využívat `<sstream>` je podporována.  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[istringstream –](../standard-library/sstream-typedefs.md#istringstream)|Umožňuje vytvořit typ `basic_istringstream` specializované na `char` parametr šablony.|  
|[ostringstream –](../standard-library/sstream-typedefs.md#ostringstream)|Umožňuje vytvořit typ `basic_ostringstream` specializované na `char` parametr šablony.|  
|[stringbuf –](../standard-library/sstream-typedefs.md#stringbuf)|Umožňuje vytvořit typ `basic_stringbuf` specializované na `char` parametr šablony.|  
|[stringstream –](../standard-library/sstream-typedefs.md#stringstream)|Umožňuje vytvořit typ `basic_stringstream` specializované na `char` parametr šablony.|  
|[wistringstream –](../standard-library/sstream-typedefs.md#wistringstream)|Umožňuje vytvořit typ `basic_istringstream` specializované na `wchar_t` parametr šablony.|  
|[wostringstream –](../standard-library/sstream-typedefs.md#wostringstream)|Umožňuje vytvořit typ `basic_ostringstream` specializované na `wchar_t` parametr šablony.|  
|[wstringbuf –](../standard-library/sstream-typedefs.md#wstringbuf)|Umožňuje vytvořit typ `basic_stringbuf` specializované na `wchar_t` parametr šablony.|  
|[wstringstream –](../standard-library/sstream-typedefs.md#wstringstream)|Umožňuje vytvořit typ `basic_stringstream` specializované na `wchar_t` parametr šablony.|  
  
### <a name="manipulators"></a>Manipulátory  
  
|||  
|-|-|  
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Výměny hodnoty mezi dvěma `sstream` objekty.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_stringbuf –](../standard-library/basic-stringbuf-class.md)|Popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, do a z pořadí prvků, které jsou uložené v objektu array.|  
|[basic_istringstream –](../standard-library/basic-istringstream-class.md)|Popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, a jehož elementy jsou přidělena přidělení třídy `Alloc`.|  
|[basic_ostringstream –](../standard-library/basic-ostringstream-class.md)|Popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, a jehož elementy jsou přidělena přidělení třídy `Alloc`.|  
|[basic_stringstream –](../standard-library/basic-stringstream-class.md)|Popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, a jehož elementy jsou přidělena přidělení třídy `Alloc`.|  
  
## <a name="requirements"></a>Požadavky  
  
- **Záhlaví:** \<sstream – >  
  
- **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



