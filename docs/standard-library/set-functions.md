---
title: '&lt;nastavit&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 65d3f4ef95ee3768323e3b727b9745a1a812f27c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltsetgt-functions"></a>&lt;nastavit&gt; funkce
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multiset)](#swap_multiset)|  
  
##  <a name="swap"></a>  swap (map)
 Vymění prvky dvou sad.  
  
```
template <class Key, class Traits, class Allocator>  
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Sada poskytuje elementy pro si místo nebo sadu, jehož elementy jsou k výměně s těmi, která sada `left`.  
  
 `left`  
 Sada, jehož elementy jsou k výměně s těmi, která sada `right`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony je algoritmus specializuje na nastavení pro spuštění funkce člena třídy kontejneru `left.` [swap](../standard-library/set-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony  
  
 `template` \< **classT**> **void swap**( **T &**, **T &**)  
  
 v algoritmu třída funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad kódu pro třídu člen [set::swap](../standard-library/set-class.md#swap) příklad použití šablony verze `swap`.  
  
##  <a name="swap_multiset"></a>  swap (multiset)
 Elementy dvě multisets výměny.  
  
```
template <class Key, class Traits, class Allocator>  
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Multimnožina poskytuje prvky, které mají být prohodily nebo multiset, jehož elementy jsou k výměně s těmi, která multimnožina `left`.  
  
 `left`  
 Multimnožina, jehož elementy jsou k výměně s těmi, která multimnožina `right`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony je algoritmus specializuje na multiset – třída kontejneru pro spuštění funkce člen `left.` [swap](../standard-library/multiset-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony  
  
 `template` \< **classT**> **void swap**( **T &**, **T &**)  
  
 v algoritmu třída funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad kódu pro třídu člen [multiset::swap](../standard-library/multiset-class.md#swap)příklad použití šablony verze `swap`.  
  
## <a name="see-also"></a>Viz také  
 [\<set>](../standard-library/set.md)



