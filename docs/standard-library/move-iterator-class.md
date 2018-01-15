---
title: "move_iterator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
dev_langs: C++
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54691a7d25e9229143e17476d5e0e09c6732e69e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="moveiterator-class"></a>move_iterator – třída
Šablona třídy `move_iterator` je obálku pro iterace. Iterátor move_iterator poskytuje stejné chování jako iterátor, kterého zabalí (uloží). Výjimkou je, že operátor přesměrování uloženého iterátoru mění na odkaz hodnoty rvalue a kopírování se tak mění na přesunutí. Další informace o rvalue najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="syntax"></a>Syntaxe  
```
class move_iterator;  
```
## <a name="remarks"></a>Poznámky  
 Třída šablony popisuje objekt, který se chová jako iterátor, kromě přesměrovávání. Ukládá náhodný přístup iterator typu `Iterator`, přístupu prostřednictvím – členská funkce `base()`. Všechny operace v `move_iterator` se provádí přímo na uložené iterator s tím rozdílem, že výsledek `operator*` je implicitně převést na `value_type&&` aby deklarátor odkazu.  
  
 A `move_iterator` může být schopný operací, které nejsou zabalené iterator definované. Tyto operace by neměly být použity.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[move_iterator –](#move_iterator)|V konstruktoru pro objekty typu `move_iterator`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[iterator_type –](#iterator_type)|Synonymum pro parametr šablony `RandomIterator`.|  
|[iterator_category –](#iterator_category)|Synonymum déle `typename` výraz se stejným názvem, `iterator_category` identifikuje obecné schopnosti iteraci.|  
|[value_type](#value_type)|Synonymum déle `typename` výraz se stejným názvem, `value_type` popisuje, jaké typy iterator prvky jsou.|  
|[difference_type –](#difference_type)|Synonymum déle `typename` výraz se stejným názvem, `difference_type` popisuje typ integrální požadované hodnoty express rozdíl mezi elementy.|  
|[ukazatele](#pointer)|Synonymum pro parametr šablony `RandomIterator`.|  
|[referenční dokumentace](#reference)|Jedná o synonymum `rvalue` odkaz `value_type&&`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[base](#base)|Členská funkce vrátí uložené iterator zabalen to `move_iterator`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[move_iterator::Operator *](#op_star)|Vrátí`(reference)*base().`|  
|[move_iterator::Operator ++](#op_add_add)|Zvýší uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před přírůstkem nebo po přírůstku.|  
|[move_iterator::Operator--](#operator--)|Sníží uložený iterátor. Přesné chování závisí na tom, zda se jedná o operaci před snížením nebo po snížení.|  
|[move_iterator::Operator-&gt;](#operator-_gt)|Vrátí `&**this`.|  
|[move_iterator::Operator-](#operator-)|Vrátí `move_iterator(*this) -=` podle první odečtením pravém hodnotu z aktuální pozici.|  
|[move_iterator::Operator]](#op_at)|Vrátí `(reference)*(*this + off)`. Umožňuje určit posun od aktuálního základu k získání hodnoty v tomto umístění.|  
|[move_iterator::Operator +](#op_add)|Vrátí `move_iterator(*this) +=` hodnotu. Umožňuje přidat posun k základu k získání hodnoty v tomto umístění.|  
|[move_iterator::Operator +=](#op_add_eq)|Přidá pravém hodnotu uložené iterator a vrátí `*this`.|  
|[move_iterator::Operator-=](#operator-_eq)|Odečte pravém hodnotu z uložené iterator a vrátí `*this`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** – std  
  
##  <a name="base"></a>move_iterator::Base  
 Vrátí uložené iterator pro tento `move_iterator`.  
  
```
RandomIterator base() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí uložené iterator.  
  
##  <a name="difference_type"></a>move_iterator::difference_type  
 Typ `difference_type` je `move_iterator` `typedef` podle znak iterator `difference_type`a zaměnitelné s ním.  
  
```
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```    
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro znak iterator `typename iterator_traits<RandomIterator>::pointer`.  
  
##  <a name="iterator_category"></a>move_iterator::iterator_category  
 Typ `iterator_category` je `move_iterator` `typedef` podle znak iterator `iterator_category`a zaměnitelné s ním.  
  
```
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```    
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro znak iterator `typename iterator_traits<RandomIterator>::iterator_category`.  
  
##  <a name="iterator_type"></a>move_iterator::iterator_type  
 Typ `iterator_type` je založena na parametr šablony `RandomIterator` pro šablony třídy `move_iterator`a zaměnitelné na příslušné místo.  
  
```
typedef RandomIterator iterator_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `RandomIterator`.  
  
##  <a name="move_iterator"></a>move_iterator::move_iterator  
 Vytvoří move iterator. Parametr se používá jako uložené iterator.  
  
```
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Iterator chcete použít jako uložené iterator.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje uložené iterator s jeho výchozí konstruktor. Zbývající konstruktory inicializovat uložené iterator s `base.base()`.  
  
##  <a name="op_add_eq"></a>move_iterator::Operator +=  
 Přidá posun do uložené iterator tak, aby uložené iterator odkazuje na element v nové aktuální umístění. Operátor pak se posouvá nové aktuálního elementu.  
  
```
move_iterator& operator+=(difference_type _Off);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Posun přidat nové aktuální stav můžete zjistit na aktuální pozici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nový aktuálního elementu.  
  
### <a name="remarks"></a>Poznámky  
 Operátor přidá `_Off` k uložené iterator. Vrátí `*this`.  
  
##  <a name="move_iterator__operator-_eq"></a>move_iterator::Operator-=  
 Přesune mezi zadaný počet předchozích elementů. Tento operátor odečítá posun z uložené iterator.  
  
```
move_iterator& operator-=(difference_type _Off);
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
 Operátor vyhodnotí `*this += -_Off`. Vrátí `*this`.  
  
##  <a name="op_add_add"></a>move_iterator::Operator ++  
 Zvýší uložené iterator, který patří k tomuto `move_iterator.` aktuálního elementu přistupuje postincrement operátor. Na další prvek přistupuje preincrement operátor.  
  
```
move_iterator& operator++();
move_iterator operator++(int);
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
 První (preincrement) operátor zvýší uložené iterator. Vrátí `*this`.  
  
 Druhý operátor (postincrement) vytvoří kopii `*this`, vyhodnotí `++*this`. Vrátí kopii.  
  
##  <a name="op_add"></a>move_iterator::Operator +  
 Vrátí pozici iterator advanced libovolný počet elementů.  
  
```
move_iterator operator+(difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátor `move_iterator(*this) +=` `_Off`.  
  
##  <a name="op_at"></a>move_iterator::Operator]  
 Umožňuje přístup k poli indexu na elementy napříč celou škálu `move iterator`.  
  
```
reference operator[](difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátor `(reference)*(*this + _Off)`.  
  
##  <a name="move_iterator__operator--"></a>move_iterator::Operator--  
 Operátory předběžné a postdecrement členy provést snížení uložené iterator.  
  
```
move_iterator& operator--();
move_iterator operator--();
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
 První – operátor (predecrement) snižuje člen uložené iterator. Vrátí `*this`.  
  
 Druhý operátor (postdecrement) vytvoří kopii `*this`, vyhodnotí `--*this`. Vrátí kopii.  
  
##  <a name="move_iterator__operator-"></a>move_iterator::Operator-  
 Snižuje uložené iterator a vrátí uvedenou hodnotu.  
  
```
move_iterator operator-(difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátor `move_iterator(*this) -= _Off`.  
  
##  <a name="op_star"></a>move_iterator::Operator *  
 Dereferences uložené iterator a vrátí hodnotu. To se chová stejně jako `rvalue reference` a provede přesun přiřazení. Operátor přenáší aktuálního elementu mimo základní iterator. Element, který následuje stane nový aktuálního elementu.  
  
```
reference operator*() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátor `(reference)*base()`.  
  
##  <a name="move_iterator__operator-_gt"></a>move_iterator::Operator-&gt;  
 Jako normální `RandomIterator` `operator->`, poskytuje přístup k pole, které patří k aktuálnímu elementu.  
  
```
pointer operator->() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí operátor `&**this`.  
  
##  <a name="pointer"></a>move_iterator::Pointer  
 Typ `pointer` je `typedef` podle náhodných iterator `RandomIterator` pro `move_iterator`a zaměnitelné.  
  
```
typedef RandomIterator  pointer;
```    
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `RandomIterator`.  
  
##  <a name="reference"></a>move_iterator::Reference  
 Typ `reference` je `typedef` na základě `value_type&&` pro `move_iterator`a zaměnitelné s `value_type&&`.  
  
```
typedef value_type&& reference;
```    
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum `value_type&&`, což je deklarátor odkazu.  
  
##  <a name="value_type"></a>move_iterator::value_type  
 Typ `value_type` je `move_iterator` `typedef` podle znak iterator `value_type`a zaměnitelné s ním.  
  
```
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```    
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro znak iterator `typename iterator_traits<RandomIterator>::value_type`.  
  
## <a name="see-also"></a>Viz také  
 [\<iterator >](../standard-library/iterator.md)   
 [Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [Konstruktory a operátory přiřazení pro přesunutí (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)




