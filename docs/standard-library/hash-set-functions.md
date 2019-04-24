---
title: '&lt;hash_set –&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 05a7ffd1e3bf02a88fe6a6cce841a440550c1057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159129"
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set –&gt; funkce

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  Prohození

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vymění prvky dvou hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Hash_set – poskytující prvky pro záměnu nebo hash_set, jehož prvky mají vyměnit s těmi hash_set *levé*.

*doleva*<br/>
Hash_set –, jehož prvky mají vyměnit s těmi hash_set *správné*.

### <a name="remarks"></a>Poznámky

`swap` Funkce šablon je algoritmus specializované na hash_set – třídy kontejnerů ke spuštění funkce člena `left.` [prohození](../standard-library/hash-set-class.md#swap)(`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablon

**Šablona \<třída T > void odkládacího souboru (T &, T &),**

Třída v algoritmu funguje tak, že přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro člen třídy [hash_set::swap](../standard-library/hash-set-class.md#swap) příklad, který používá verzi šablony `swap`.

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vymění prvky dvou hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Hash_multiset – poskytující prvky pro záměnu nebo hash_multiset, jehož prvky mají vyměnit s těmi hash_multiset *levé*.

*doleva*<br/>
Hash_multiset –, jehož prvky mají vyměnit s těmi hash_multiset *správné*.

### <a name="remarks"></a>Poznámky

`swap` Funkce šablon je algoritmus specializované na hash_multiset – třídy kontejnerů ke spuštění funkce člena `left.` [prohození](../standard-library/hash-multiset-class.md#swap)(`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablon

**Šablona \<třída T > void odkládacího souboru (T &, T &),**

Třída v algoritmu funguje tak, že přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro člen třídy [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) příklad, který používá verzi šablony `swap`.

## <a name="see-also"></a>Viz také:

[<hash_set>](../standard-library/hash-set.md)<br/>
