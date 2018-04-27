---
title: '&lt;hash_set –&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: d9dc03b6ea4e6ed90a6eda433faf6710b6982bb3
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set –&gt; funkce

|||
|-|-|
|[Swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  Swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Elementy dvě hash_sets výměny.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_set – poskytuje prvky, které mají být prohodily nebo hash_set, jehož elementy jsou k výměně s těmi hash_set `left`.

`left` Hash_set, jehož elementy jsou k výměně s těmi hash_set `right`.

### <a name="remarks"></a>Poznámky

`swap` Funkce šablony je algoritmus specializuje na hash_set – třída kontejneru pro spuštění funkce člen `left.` [swap](../standard-library/hash-set-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony

**Šablona \<třída T > void odkládacího souboru (T & T &),**

v algoritmu třída funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu člen [hash_set::swap](../standard-library/hash-set-class.md#swap) pro příklad, který používá verzi šablony služby `swap`.

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Elementy dvě hash_multisets výměny.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Hash_multiset – poskytuje prvky, které mají být prohodily nebo hash_multiset, jehož elementy jsou k výměně s těmi hash_multiset `left`.

`left` Hash_multiset –, jehož elementy jsou k výměně s těmi hash_multiset `right`.

### <a name="remarks"></a>Poznámky

`swap` Funkce šablony je algoritmus specializuje na hash_multiset – třída kontejneru pro spuštění funkce člen `left.` [swap](../standard-library/hash-multiset-class.md#swap)( `right`). Toto je instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony

**Šablona \<třída T > void odkládacího souboru (T & T &),**

v algoritmu třída funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu člen [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) pro příklad, který používá verzi šablony služby `swap`.

## <a name="see-also"></a>Viz také

[<hash_set>](../standard-library/hash-set.md)<br/>
