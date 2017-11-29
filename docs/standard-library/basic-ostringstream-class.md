---
title: "basic_ostringstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs: C++
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a5d494d28872bf5e59f0c436ceb037bd36a94c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="basicostringstream-class"></a>basic_ostringstream – třída
Popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_ostringstream : public basic_ostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Alloc`  
 Třída alokátoru  
  
 `Elem`  
 Typ elementu základní řetězce.  
  
 *Tr*  
 Vlastnosti znak specializované na základní prvek řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Třída popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**a jehož elementy jsou přidělena přidělení třídy `Alloc`. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_ostringstream –](#basic_ostringstream)|Vytvoří objekt typu `basic_ostringstream`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type –](#allocator_type)|Typ je synonymum pro parametr šablony `Alloc`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[rdbuf –](#rdbuf)|Vrátí adresu uložené datového proudu vyrovnávací paměti typu `pointer` k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|  
|[str –](#str)|Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<sstream – >  
  
 **Namespace:** – std  
  
##  <a name="allocator_type"></a>basic_ostringstream::allocator_type  
 Typ je synonymum pro parametr šablony `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream  
 Vytvoří objekt basic_ostringstream typu.  
  
```  
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Objekt typu `basic_string`.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základní třídu voláním [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), kde **sb** je objekt uložené třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Také inicializuje **sb** ve volání basic_stringbuf < **Elem**, **Tr**, `Alloc`> ( `_Mode` &#124; `ios_base::out`).  
  
 Druhý konstruktor inicializuje základní třídu volání basic_ostream ( **sb**). Také inicializuje **sb** ve volání basic_stringbuf < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out`).  
  
##  <a name="rdbuf"></a>basic_ostringstream::rdbuf  
 Vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k basic_stringbuf < **Elem**, **Tr**, `Alloc`>.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k basic_stringbuf < **Elem**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.  
  
##  <a name="str"></a>basic_ostringstream::str  
 Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.  
  
```  
basic_string<Elem, Tr, Alloc> str() const;

 
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newstr`  
 Nový řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, jehož kopii pořadí řízené je řízené sekvenci  **\*to**.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první členská funkce [rdbuf –](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Druhé volání funkce člen `rdbuf`  ->  **str**( `_Newstr`).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) pro příklad, který používá **str**.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)
