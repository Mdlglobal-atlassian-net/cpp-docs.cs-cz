---
title: "regex_token_iterator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29d8186911b51865de06b24e675a9570e3ea04cc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="regextokeniterator-class"></a>regex_token_iterator – třída
Iterator – třída pro submatches.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator {  
public:  
   typedef basic_regex<Elem, RXtraits> regex_type;  
   typedef sub_match<BidIt> value_type;  
   typedef std::forward_iterator_tag iterator_category;  
   typedef std::ptrdiff_t difference_type;  
   typedef const sub_match<BidIt> *pointer;  
   typedef const sub_match<BidIt>& reference;  
   regex_token_iterator();
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, int submatch = 0,  
      regex_constants::match_flag_type f = regex_constants::match_default);
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, const std::vector<int> submatches,  
      regex_constants::match_flag_type f = regex_constants::match_default);
   template <std::size_t N>  
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, const int (&submatches)[N],  
      regex_constants::match_flag_type f = regex_constants::match_default);
   bool operator==(const regex_token_iterator& right);
   bool operator!=(const regex_token_iterator& right);
   const basic_string<Elem>& operator*();
   const basic_string<Elem> * operator->();
   regex_token_iterator& operator++();
   regex_token_iterator& operator++(int);
private:  
   regex_iterator<BidIt, Elem, RXtraits> it; // exposition only  
   vector<int> subs;   // exposition only  
   int pos;  // exposition only  
   };  
```  
#### <a name="parameters"></a>Parametry  
 `BidIt`  
 Typ iterator submatches.  
  
 `Elem`  
 Typ prvků, které se mají spárovat.  
  
 `RXtraits`  
 Třída vlastností prvků.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje konstantní dopředného iterator objektu. Koncepčně, obsahuje `regex_iterator` objekt, který se používá k hledání regulárního výrazu odpovídá v posloupnost znaků. Extrahuje objekty typu `sub_match<BidIt>` představující submatches identifikovaný index hodnoty v uložené vektoru `subs` pro každý shoda s regulárním výrazem.  
  
 Hodnota indexu -1 označuje posloupnost znaků od ihned po konci předchozího regulární výraz text, nebo od začátku posloupnost znaků, pokud neodpovídá žádná předchozí regulární výraz a rozšíření do, ale ne Pokud není nalezena žádná aktuální shoda, včetně první znak aktuální shoda s regulárním výrazem, nebo na konec posloupnost znaků. Žádné jiné hodnoty indexu `idx` označí obsah skupiny zachycení uchovávat v `it.match[idx]`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<regex >  
  
 **Namespace:** – std  
  
##  <a name="difference_type"></a>  regex_token_iterator::difference_type  
 Typ iterator rozdíl.  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `std::ptrdiff_t`.  
  
### <a name="example"></a>Příklad  
  
```cpp    
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
```  
  
##  <a name="iterator_category"></a>  regex_token_iterator::iterator_category  
 Typ kategorie iterator.  
  
```  
typedef std::forward_iterator_tag iterator_category;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `std::forward_iterator_tag`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_iterator_category.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_neq"></a>  regex_token_iterator::operator!=  
 Porovná nerovnost iterátory.  
  
```  
bool operator!=(const regex_token_iterator& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Iterator pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `!(*this == right)`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_star"></a>  regex_token_iterator::operator*  
 Přístup k určené submatch.  
  
```  
const sub_match<BidIt>& operator*();
```  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `sub_match<BidIt>` objekt reprezentující skupinou zachycení identifikuje hodnotu indexu `subs[pos]`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_operator_star.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_add_add"></a>  regex_token_iterator::operator++  
 Zvýší iteraci.  
  
```  
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud uložené iterator `it` je iterátor koncová sekvence první operátor nastaví uložené hodnoty `pos` na hodnotu `subs.size()` (díky čemuž iterovat koncová sekvence). V opačném případě operátor zvýší uložené hodnoty `pos`; Pokud je výsledek rovna hodnotě `subs.size()` nastaví uložené hodnoty `pos` na hodnotu nula a zvýší uložené iterator `it`. Pokud zvyšování nechá uložené iterator nerovné k iterátor koncová sekvence operátor dělá nic dalšího. Jinak, pokud byl konec předchozí shoda na konci posloupnost znaků operátor nastaví uložené hodnotu `pos` k `subs.size()`. Jinak, operátor opakovaně zvýší uložené hodnoty `pos` dokud `pos == subs.size()` nebo `subs[pos] == -1` (čímž zajišťuje, že na další dereference iterator Pokud jedna z hodnot indexu je -1 vrátí konec posloupnost znaků). Ve všech případech operátor vrátí objekt.  
  
 Druhý operátor vytvoří kopii objektu, zvýší objektu a pak vrátí kopie.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_operator_inc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_eq_eq"></a>  regex_token_iterator::operator==  
 Porovná iterátory rovnosti.  
  
```  
bool operator==(const regex_token_iterator& right);
```  
  
### <a name="parameters"></a>Parametry  
 vpravo  
 Iterator pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `it == right.it && subs == right.subs && pos == right.pos`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_operator_eq.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="regex_token_iterator__operator-_gt"></a>  regex_token_iterator::operator-&gt;  
 Přístup k určené submatch.  
  
```  
const sub_match<BidIt> * operator->();
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí ukazatel `sub_match<BidIt>` objekt reprezentující skupinou zachycení identifikuje hodnotu indexu `subs[pos]`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_operator_arrow.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="pointer"></a>  regex_token_iterator::Pointer  
 Typ ukazatele na shodu.  
  
```  
typedef sub_match<BidIt> *pointer;  
```  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_pointer.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `sub_match<BidIt>*`, kde `BidIt` je parametr šablony.  
  
##  <a name="reference"></a>  regex_token_iterator::Reference  
 Typ odkaz na submatch.  
  
```  
typedef sub_match<BidIt>& reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `sub_match<BidIt>&`, kde `BidIt` je parametr šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="regex_token_iterator"></a>  regex_token_iterator::regex_token_iterator  
 Vytvoří iteraci.  
  
```  
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, int submatch = 0,  
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, const vector<int> submatches,  
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>  
regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, const int (&submatches)[N],  
    regex_constants::match_flag_type f = regex_constants::match_default);
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Začátek pořadí tak, aby odpovídaly.  
  
 `last`  
 Konec pořadí tak, aby odpovídaly.  
  
 `re`  
 Regulární výraz pro odpovídající položky.  
  
 `f`  
 Příznaky pro odpovídající položky.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktoru vytvoří iterovat koncová sekvence.  
  
 Druhý konstruktor vytvoří objekt, jehož uložené iterator `it` je inicializováno `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jejichž uložené vektoru `subs` obsahuje přesně jeden celé číslo s hodnotou `submatch`a jehož uložené hodnoty `pos` je nulová. Poznámka: výsledný objekt extrahuje submatch identifikovaný hodnotu indexu `submatch` pro každé úspěšné regulárního výrazu shody.  
  
 Třetí konstruktoru vytvoří objekt, jehož uložené iterator `it` je inicializováno `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jejichž uložené vektoru `subs` obsahuje kopii argument konstruktoru `submatches`a jehož uložené hodnoty `pos` je nulová.  
  
 Čtvrtý konstruktoru vytvoří objekt jehož uložené iterator `it` je inicializováno `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jejichž uložené vektoru `subs` obsahuje `N` hodnoty ukazuje argument konstruktoru `submatches`a jehož uložené Hodnota `pos` je nulová.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="regex_type"></a>  regex_token_iterator::regex_type  
 Typ odpovídající regulární výraz.  
  
```  
typedef basic_regex<Elem, RXtraits> regex_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typedef se jedná o synonymum `basic_regex<Elem, RXtraits>`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_regex_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="value_type"></a>  regex_token_iterator::value_type  
 Typ submatch.  
  
```  
typedef sub_match<BidIt> value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `sub_match<BidIt>`, kde `BidIt` je parametr šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__regex__regex_token_iterator_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
## <a name="see-also"></a>Viz také  
[\<regex>](../standard-library/regex.md)  
[regex_constants – třída](../standard-library/regex-constants-class.md)  
[regex_error – třída](../standard-library/regex-error-class.md)  
[\<regulární výraz > funkce](../standard-library/regex-functions.md)  
[regex_iterator – třída](../standard-library/regex-iterator-class.md)  
[\<regulární výraz > operátory](../standard-library/regex-operators.md)  
[regex_traits – třída](../standard-library/regex-traits-class.md)  
[\<regulární výraz > Definice TypeDef](../standard-library/regex-typedefs.md)  

