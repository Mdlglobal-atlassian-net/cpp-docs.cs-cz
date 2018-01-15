---
title: "match_results – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: regex/std::match_results
dev_langs: C++
helpviewer_keywords: match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f0fa4ea48a9947492ee4ce53f33450d1944d6d3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="matchresults-class"></a>match_results – třída
Obsahuje posloupnost submatches.  
  
## <a name="syntax"></a>Syntaxe  
```  
class match_results {  
   public:  
   explicit match_results(const Alloc& alloc = Alloc());
   match_results(const match_results& right);
   match_results& operator=(const match_results& right);
   difference_type position(size_type sub = 0) const;
   difference_type length(size_type sub = 0) const;
   string_type str(size_type sub = 0) const;
   const_reference operator[](size_type n) const;
   const_reference prefix() const;
   const_reference suffix() const;
   const_iterator begin() const;
   const_iterator end() const;
   template <class OutIt>  
   OutIt format(OutIt out,  
   const string_type& fmt, match_flag_type flags = format_default) const;
   string_type format(const string_type& fmt,  
   match_flag_type flags = format_default) const;
   allocator_type get_allocator() const;
   void swap(const match_results& other) throw();
   size_type size() const;
   size_type max_size() const;
   bool empty() const;
   typedef sub_match<BidIt>  
   value_type;  
   typedef const typename Alloc::const_reference const_reference;  
   typedef const_reference reference;  
   typedef T0 const_iterator;  
   typedef const_iterator iterator;  
   typedef typename iterator_traits<BidIt>::difference_type difference_type;  
   typedef typename Alloc::size_type size_type;  
   typedef Alloc allocator_type;  
   typedef typename iterator_traits<BidIt>::value_type char_type;  
   typedef basic_string<char_type> string_type;  
   };  
```  
#### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iterator submatches.  
  
 `Alloc`  
 Typ alokátoru pro správu úložiště  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který řídí neměnitelný posloupnost elementy typu `sub_match<BidIt>` generované hledání regulárního výrazu. Každý prvek se odkazuje na dalším, který odpovídá skupině zachycení odpovídající daný element.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<regex >  
  
 **Namespace:** – std  
  
##  <a name="allocator_type"></a>match_results::allocator_type  
 Typ alokátoru pro správu úložiště  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef je synonymum argumentu šablony `Alloc`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_allocator_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="begin"></a>match_results::begin  
 Označuje začátek submatch pořadí.  
  
```  
const_iterator begin() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí iterator náhodný přístup tohoto body v prvním elementem pořadí (nebo jenom přesahuje za konec prázdnou sekvencí).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_begin.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="char_type"></a>match_results::char_type  
 Typ prvku  
  
```  
typedef typename iterator_traits<BidIt>::value_type char_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef je synonymum pro typ `iterator_traits<BidIt>::value_type`, což je typ elementu posloupnost znaků, který je vyhledán.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_char_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="const_iterator"></a>match_results::const_iterator  
 Const typ iterator submatches.  
  
```  
typedef T0 const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef popisuje objekt, který může sloužit jako konstantní iterator náhodný přístup pro řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_const_iterator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="const_reference"></a>match_results::const_reference  
 Typ const odkaz na element.  
  
```  
typedef const typename Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef popisuje objekt, který může sloužit jako konstantní odkaz na element řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_const_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="difference_type"></a>match_results::difference_type  
 Typ iterator rozdíl.  
  
```  
typedef typename iterator_traits<BidIt>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef je synonymum pro typ `iterator_traits<BidIt>::difference_type`; popisuje objekt, který může představovat rozdíl mezi jakékoli dvě iterátory, které odkazují na elementy řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_difference_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="empty"></a>match_results::Empty  
 Testy pro žádné submatches.  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pouze v případě, že hledání regulárního výrazu se nezdařilo.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_empty.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="end"></a>match_results::end  
 Označuje konec submatch pořadí.  
  
```  
const_iterator end() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí iterovat této body právě přesahuje za konec sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_end.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="format"></a>match_results::Format  
 Formátuje dílčí shody.  
  
```  
template <class OutIt>  
OutIt format(OutIt out,  
    const string_type& fmt, match_flag_type flags = format_default) const;

 
string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```  
  
### <a name="parameters"></a>Parametry  
 `OutIt`  
 Typ výstupního iterátoru.  
  
 `out`  
 Výstupní tok, do kterého se má zapisovat.  
  
 `fmt`  
 Řetězec formátu.  
  
 `flags`  
 Příznaky formátu.  
  
### <a name="remarks"></a>Poznámky  
 Každý člen funkce generuje formátovaný text pod kontrolou formátu `fmt`. První člen funkce zapíše formátovaný text pořadí definované její argument `out` a vrátí `out`. Druhá členská funkce vrátí objekt řetězce s kopií formátovaného textu.  
  
 Ke generování formátovaný text. literál text ve formátovacím řetězci je běžným zkopírován do cílové sekvence. Každá sekvence escape v řetězci formátu je nahrazena textem, který reprezentuje. Podrobnosti kopírování a nahrazování jsou ovládány příznaky formátu předanými funkci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_format.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="get_allocator"></a>match_results::get_allocator  
 Vrátí uložené přidělení.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí kopii objekt allocator používá `*this` přidělit jeho `sub_match` objekty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_get_allocator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="iterator"></a>match_results::iterator  
 Typ iterator submatches.  
  
```  
typedef const_iterator iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako iterator náhodný přístup pro řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_iterator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="length"></a>match_results::length  
 Vrátí délku submatch.  
  
```  
difference_type length(size_type sub = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `sub`  
 Index submatch.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `(*this)[sub].length()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_length.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="match_results"></a>match_results::match_results  
 Vytvoří objekt.  
  
```  
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```  
  
### <a name="parameters"></a>Parametry  
 `alloc`  
 Objekt alokátoru, který se má uložit.  
  
 `right`  
 Match_results – objekt pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 První konstrukce konstruktor `match_results` objekt, který obsahuje žádné submatches. Druhý konstruktor konstrukce `match_results` objekt, který je kopií `right`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="max_size"></a>match_results::max_size  
 Získá největší počet submatches.  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku nejdelší pořadí, které můžete řídit objekt.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_max_size.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="op_eq"></a>match_results::Operator =  
 Zkopírování objektu match_results.  
  
```  
match_results& operator=(const match_results& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Match_results – objekt pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů nahrazuje pořadí řízené `*this` kopii pořadí řízené `right`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_operator_as.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="op_at"></a>[match_results::Operator]  
 Přístup a určitých podřízených objektů.  
  
```  
const_reference operator[](size_type n) const;
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Index submatch.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na element `n` řízené sekvenci nebo odkaz na prázdnou `sub_match` objektu Pokud `size() <= n` nebo, pokud zaznamenat skupiny `n` nebyla součástí shody.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_operator_br.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="position"></a>match_results::position  
 Získat počáteční posun podskupiny.  
  
```  
difference_type position(size_type sub = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `sub`  
 Index submatch.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `std::distance(prefix().first, (*this)[sub].first)`, který je vzdálenost od první znak v pořadí cíl na první znak v submatch na kterou odkazoval element `n` řízené pořadí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_position.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="prefix"></a>match_results::prefix  
 Získá pořadí před první submatch.  
  
```  
const_reference prefix() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na objekt typu `sub_match<BidIt>` který odkazuje na posloupnost znaků, který začíná na začátku pořadí cíl a končí na `(*this)[0].first`, to znamená, odkazuje na text, který předchází odpovídající dalším.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_prefix.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="reference"></a>match_results::Reference  
 Typ odkaz na element.  
  
```  
typedef const_reference reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro typ `const_reference`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="size"></a>match_results::size  
 Spočítá počet submatches.  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Člen funkce vrátí jeden více než počet skupin zachycení v regulárním výrazu, která byla použita pro hledání nebo nula, pokud nebyla provedena žádná vyhledávání.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_size.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="size_type"></a>match_results::size_type  
 Typ submatch počet.  
  
```  
typedef typename Alloc::size_type size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro typ `Alloc::size_type`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_size_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="str"></a>match_results::str  
 Vrátí submatch.  
  
```  
string_type str(size_type sub = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `sub`  
 Index submatch.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `string_type((*this)[sub])`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_str.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="string_type"></a>match_results::STRING_TYPE  
 Typ řetězec.  
  
```  
typedef basic_string<char_type> string_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro typ `basic_string<char_type>`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_string_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="suffix"></a>match_results::suffix  
 Získá pořadí po poslední submatch.  
  
```  
const_reference suffix() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na objekt typu `sub_match<BidIt>` který odkazuje na posloupnost znaků, který začíná na `(*this)[size() - 1].second` a končí na konci pořadí cíl, který je odkazuje na text, který následuje odpovídající dalším.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_suffix.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="swap"></a>match_results::swap  
 Zamění dva objekty match_results.  
  
```  
void swap(const match_results& right) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Match_results – objekt, který chcete Prohodit s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce prohození obsah `*this` a `right` konstantní včas a nevyvolá výjimku výjimky.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_swap.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
##  <a name="value_type"></a>match_results::value_type  
 Typ submatch.  
  
```  
typedef sub_match<BidIt> value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef je synonymum pro typ `sub_match<BidIt>`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__match_results_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::cout << "prefix: matched == " << std::boolalpha   
        << mr.prefix().matched   
        << ", value == " << mr.prefix() << std::endl;   
    std::cout << "whole match: " << mr.length() << " chars, value == "   
        << mr.str() << std::endl;   
    std::cout << "suffix: matched == " << std::boolalpha   
        << mr.suffix().matched   
        << ", value == " << mr.suffix() << std::endl;   
    std::cout << std::endl;   
  
    std::string fmt("\"c(a*)|(b)\" matched \"$0\"\n"   
        "\"(a*)\" matched \"$1\"\n"   
        "\"(b)\" matched \"$2\"\n");   
    std::cout << mr.format(fmt) << std::endl;   
    std::cout << std::endl;   
  
// index through submatches   
    for (size_t n = 0; n < mr.size(); ++n)   
        {   
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha   
            << mr[n].matched <<   
            " at position " << mr.position(n) << std::endl;   
        std::cout << "  " << mr.length(n)   
            << " chars, value == " << mr[n] << std::endl;   
        }   
    std::cout << std::endl;   
  
// iterate through submatches   
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)   
        {   
        std::cout << "next submatch: matched == " << std::boolalpha   
            << it->matched << std::endl;   
        std::cout << "  " << it->length()   
            << " chars, value == " << *it << std::endl;   
        }   
    std::cout << std::endl;   
  
// other members   
    std::cmatch mr1(mr);   
    mr = mr1;   
    mr.swap(mr1);   
  
    char buf[10];   
 *mr.format(&buf[0], "<$0>") = '\0';   
    std::cout << &buf[0] << std::endl;   
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;   
  
    std::cmatch::allocator_type al = mr.get_allocator();   
    std::cmatch::string_type str = std::string("x");   
    std::cmatch::size_type maxsiz = mr.max_size();   
    std::cmatch::char_type ch = 'x';   
    std::cmatch::difference_type dif = mr.begin() - mr.end();   
    std::cmatch::const_iterator cit = mr.begin();   
    std::cmatch::value_type val = *cit;   
    std::cmatch::const_reference cref = val;   
    std::cmatch::reference ref = val;   
  
    maxsiz = maxsiz;  // to quiet "unused" warnings   
    if (ref == cref)   
        ch = ch;   
    dif = dif;   
  
    return (0);   
    }  
  
```  
  
```Output  
prefix: matched == true, value == x  
whole match: 4 chars, value == caaa  
suffix: matched == true, value == y  
  
"c(a*)|(b)" matched "caaa"  
"(a*)" matched "aaa"  
"(b)" matched ""  
  
submatch[0]: matched == true at position 1  
  4 chars, value == caaa  
submatch[1]: matched == true at position 2  
  3 chars, value == aaa  
submatch[2]: matched == false at position 6  
  0 chars, value ==   
  
next submatch: matched == true  
  4 chars, value == caaa  
next submatch: matched == true  
  3 chars, value == aaa  
next submatch: matched == false  
  0 chars, value ==   
  
<caaa>  
empty == false  
```  
  
## <a name="see-also"></a>Viz také  
 [\<regulární výraz >](../standard-library/regex.md)


