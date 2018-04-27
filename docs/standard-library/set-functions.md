---
title: '&lt;nastavit&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: 29579adf6b9556635862985b324e27ebea416bc0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltsetgt-functions"></a>&lt;nastavit&gt; funkce

|||
|-|-|
|[swap (map)](#swap)|[swap (multiset)](#swap_multiset)|

## <a name="swap"></a>  swap (map)

Vymění prvky dvou sad.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Sada poskytuje elementy pro si místo nebo sadu, jehož elementy jsou k výměně s těmi, která sada `left`.

`left` Sada, jehož elementy jsou k výměně s těmi, která sada `right`.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializuje na nastavení pro spuštění funkce člena třídy kontejneru `left.` [swap](../standard-library/set-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony

`template` \< **classT**> **void swap**( **T &**, **T &**)

v algoritmu třída funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu člen [set::swap](../standard-library/set-class.md#swap) příklad použití šablony verze `swap`.

## <a name="swap_multiset"></a>  swap (multiset)

Elementy dvě multisets výměny.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Multimnožina poskytuje prvky, které mají být prohodily nebo multiset, jehož elementy jsou k výměně s těmi, která multimnožina `left`.

`left` Multimnožina, jehož elementy jsou k výměně s těmi, která multimnožina `right`.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializuje na multiset – třída kontejneru pro spuštění funkce člen `left.` [swap](../standard-library/multiset-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony

`template` \< **classT**> **void swap**( **T &**, **T &**)

v algoritmu třída funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu člen [multiset::swap](../standard-library/multiset-class.md#swap)příklad použití šablony verze `swap`.

## <a name="see-also"></a>Viz také

[\<set>](../standard-library/set.md)<br/>
