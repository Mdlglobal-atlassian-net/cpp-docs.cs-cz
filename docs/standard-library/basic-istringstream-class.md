---
title: "basic_istringstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6956b4708061c5eb18ec2adf1570920980dd17e1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="basicistringstream-class"></a>basic_istringstream – třída
Popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_istringstream : public basic_istream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Alloc`  
 Třída alokátoru  
  
 `Elem`  
 Typ elementu základní řetězce.  
  
 *Tr*  
 Vlastnosti znak specializované na základní prvek řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, a jehož elementy jsou přidělena přidělení –Třída`Alloc`. Objekt ukládá objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_istringstream](#basic_istringstream)|Vytvoří objekt typu `basic_istringstream`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ je synonymum pro parametr šablony `Alloc`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|Vrátí adresu uložené datového proudu vyrovnávací paměti typu `pointer` k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|  
|[str](#str)|Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.|  
|[swap](#swap)|Výměny hodnoty v tomto `basic_istringstream` objekt pro u zadaného objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Přiřadí hodnoty k tomuto `basic_istringstream` objekt z objektu parametru.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<sstream – >  
  
 **Namespace:** – std  
  
##  <a name="allocator_type"></a>  basic_istringstream::allocator_type  
 Typ je synonymum pro parametr šablony `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream  
 Vytvoří objekt typu `basic_istringstream`.  
  
```  
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,  
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Objekt typu `basic_string`.  
  
 `right`  
 Rvalue odkaz `basic_istringstream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)( `sb`), kde `sb` je objekt uložené třídy [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr`, `Alloc`>. Také inicializuje `sb` voláním `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `_Mode` &#124; `ios_base::in`).  
  
 Druhý konstruktor inicializuje základní třídu voláním `basic_istream(sb)`. Také inicializuje `sb` voláním `basic_stringbuf` <  `Elem`, `Tr`, `Alloc`> ( `str`, `_Mode` &#124; `ios_base::in`).  
  
 Třetí konstruktor inicializuje objekt s obsahem `right`, považován za deklarátor odkazu.  
  
##  <a name="op_eq"></a>  basic_istringstream::Operator =  
 Přiřadí hodnoty k tomuto `basic_istringstream` objekt z objektu parametru.  
  
```  
basic_istringstream& operator=(basic_istringstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Rvalue odkaz na `basic_istringstream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů nahradí obsah objektu s obsahem `right`, ošetřených jako deklarátor odkazu přesunout přiřazení.  
  
##  <a name="rdbuf"></a>  basic_istringstream::rdbuf  
 Vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k basic_stringbuf < **Elem**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.  
  
##  <a name="str"></a>  basic_istringstream::str  
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
  
##  <a name="swap"></a>  basic_istringstream::swap  
 Výměny hodnoty dva `basic_istringstream` objekty.  
  
```  
void swap(basic_istringstream& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|`lvalue` Odkaz na `basic_istringstream` objektu.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce výměny hodnoty tohoto objektu a hodnoty `right`.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

