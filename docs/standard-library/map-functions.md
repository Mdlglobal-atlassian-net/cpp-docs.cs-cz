---
title: '&lt;Mapa&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 29fa327fe892cba8c7cd9d9f4f428baa130ded29
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltmapgt-functions"></a>&lt;Mapa&gt; funkce
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|  
  
##  <a name="swap_multimap"></a>  swap (map)
 Zamění prvky dvou objektů map.  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    map<Key, Traits, Compare, Alloctor>& left,  
    map<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Mapy poskytování elementy pro si místo nebo mapy, jehož elementy jsou k výměně s těmi, která mapy `left`.  
  
 `left`  
 Mapy, jehož elementy jsou k výměně s těmi, která mapy `right`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony je algoritmus specializuje na mapě třída kontejneru provést – členská funkce `left`.[ swap](../standard-library/map-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony **šablony** \< **třída T**> **void swap**( **T &**, **T &**), v algoritmu třídy funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad kódu pro funkce člen [map::swap](../standard-library/map-class.md#swap) pro příklad, který používá verzi šablony služby `swap`.  
  
##  <a name="swap"></a>  swap (multimap)
 Elementy dvě multimaps výměny.  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,  
    multimap<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Multimap poskytuje prvky, které mají být prohodily nebo multimap, jehož elementy jsou k výměně s těmi multimap `left`.  
  
 `left`  
 Multimap, jehož elementy jsou k výměně s těmi multimap `right`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony je algoritmus specializuje na mapě třídu kontejneru pro spuštění ve multimap – třída kontejneru provést – členská funkce `left`.[ swap](../standard-library/multimap-class.md#swap) ( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony **šablony** \< **třída T**> **void swap**( **T &**, **T &**), v algoritmu třídy funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad kódu pro funkce člen [multimap::swap](../standard-library/multimap-class.md#swap) pro příklad, který používá verzi šablony služby `swap`.  
  
## <a name="see-also"></a>Viz také  
 [\<map>](../standard-library/map.md)
