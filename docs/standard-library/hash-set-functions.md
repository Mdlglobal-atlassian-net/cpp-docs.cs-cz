---
title: '&lt;hash_set&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370590"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; funkce

|||
|-|-|
|[Swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>Swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
hash_set poskytující prvky, které mají být vyměněny, nebo hash_set jejichž prvky mají být vyměněny za prvky hash_set *vlevo*.

*Vlevo*\
hash_set jejichž prvky mají být vyměněny s prvky hash_set *práva*.

### <a name="remarks"></a>Poznámky

Funkce `swap` šablony je algoritmus specializovaný na třídu kontejneru `left.`hash_set`right`pro spuštění [prohození](../standard-library/hash-set-class.md#swap)členské funkce ( ). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejspecializovanější verzi funkce šablony. Obecná verze funkce šablony

**šablona \<třídy T> void swap (T&, T&),**

ve třídě algoritmu pracuje podle přiřazení a je pomalá operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s vnitřní reprezentací třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu člena [hash_set::swap](../standard-library/hash-set-class.md#swap) pro příklad, který používá verzi šablony aplikace `swap`.

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>swap (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
hash_multiset poskytuje prvky, které mají být vyměněny, nebo hash_multiset jejichž prvky mají být vyměněny s prvky hash_multiset *vlevo*.

*Vlevo*\
hash_multiset jejichž prvky mají být vyměněny s prvky hash_multiset *pravice*.

### <a name="remarks"></a>Poznámky

Funkce `swap` šablony je algoritmus specializovaný na třídu kontejneru `left.`hash_multiset`right`pro spuštění [prohození](../standard-library/hash-multiset-class.md#swap)členské funkce ( ). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejspecializovanější verzi funkce šablony. Obecná verze funkce šablony

**šablona \<třídy T> void swap (T&, T&),**

ve třídě algoritmu pracuje podle přiřazení a je pomalá operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s vnitřní reprezentací třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu člena [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) pro příklad, který používá verzi šablony `swap`aplikace .

## <a name="see-also"></a>Viz také

[<hash_set>](../standard-library/hash-set.md)
