---
title: "&lt;vlákno&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
dev_langs: C++
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: ff0fa361845c7bf64dd15bfc4e23be7b92b6cc39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltthreadgt-operators"></a>&lt;vlákno&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|  
|[operátor&lt;](#op_lt)|[operátor&lt;&lt;](#op_lt_lt)|[operátor&lt;=](#op_lt_eq)|  
|[Operator ==](#op_eq_eq)|  
  
##  <a name="op_gt_eq"></a>operátor&gt;=  
 Určuje, zda jeden `thread::id` je větší než nebo rovna hodnotě jiný objekt.  
  
```cpp  
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread::id` objektu.  
  
 `Right`  
 Právo `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `!(Left < Right)`  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="op_gt"></a>operátor&gt;  
 Určuje, zda jeden `thread::id` je větší než druhý objekt.  
  
```cpp  
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread::id` objektu.  
  
 `Right`  
 Právo `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `Right < Left`  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="op_lt_eq"></a>operátor&lt;=  
 Určuje, zda jeden `thread::id` objektu je menší než nebo rovna do jiného.  
  
```cpp  
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread::id` objektu.  
  
 `Right`  
 Právo `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `!(Right < Left)`  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="op_lt"></a>operátor&lt;  
 Určuje, zda jeden `thread::id` objektu je menší než jiné.  
  
```cpp  
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread::id` objektu.  
  
 `Right`  
 Právo `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud `Left` předchází `Right` v celkový řazení; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Operátor definuje celkový řazení na všech `thread::id` objekty. Tyto objekty lze jako klíče v asociativní kontejnery.  
  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="op_neq"></a>Operator! =  
 Porovná dva `thread::id` objekty nerovnost.  
  
```cpp  
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread::id` objektu.  
  
 `Right`  
 Právo `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `!(Left == Right)`  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Porovná dva `thread::id` objekty rovnosti.  
  
```cpp  
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Levé straně `thread::id` objektu.  
  
 `Right`  
 Právo `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud dva objekty představují stejném vlákně, v provádění nebo pokud ani objekt představuje podproces provádění; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nevyvolá výjimku jakékoli výjimky.  
  
##  <a name="op_lt_lt"></a>operátor&lt;&lt;  
 Vloží text reprezentace `thread::id` objektu do datového proudu.  
  
```cpp  
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```  
  
### <a name="parameters"></a>Parametry  
 `Ostr`  
 A [basic_ostream](../standard-library/basic-ostream-class.md) objektu.  
  
 `Id`  
 A `thread::id` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `Ostr`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vloží `Id` do `Ostr`.  
  
 Pokud dva `thread::id` porovnat stejné objekty, vložené textové reprezentace těchto objektů jsou stejné.  
  
## <a name="see-also"></a>Viz také  
 [\<vlákno >](../standard-library/thread.md)



