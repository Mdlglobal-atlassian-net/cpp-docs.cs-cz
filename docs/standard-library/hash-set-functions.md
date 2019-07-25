---
title: '&lt;funkce&gt; hash_set'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 2fbc05c16ba6629397bbb07bab30cb9315a16e1f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448599"
---
# <a name="lthashsetgt-functions"></a>&lt;funkce&gt; hash_set

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>adresu

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Hash_set poskytuje prvky, které mají být měněny, nebo hash_set, jejichž prvky mají být vyměňovány s hash_set *doleva*.

*zbývá*\
Hash_set, jehož prvky mají být vyměňovány pomocí hash_set *práva*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru hash_set ke spuštění funkce `left.` [swapu](../standard-library/hash-set-class.md#swap)členské funkce (`right`). `swap` Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony

**Třída \<šablony T > void swap (t &, t &),**

Třída algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu member [hash_set:: swap](../standard-library/hash-set-class.md#swap) pro příklad, který používá verzi `swap`šablony.

## <a name="swap_hash_multiset"></a>swap (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Hash_multiset poskytuje prvky, které mají být měněny, nebo hash_multiset, jejichž prvky mají být vyměňovány s hash_multiset *doleva*.

*zbývá*\
Hash_multiset, jehož prvky mají být vyměňovány pomocí hash_multiset *práva*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru hash_multiset ke spuštění funkce `left.` [swapu](../standard-library/hash-multiset-class.md#swap)členské funkce (`right`). `swap` Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony

**Třída \<šablony T > void swap (t &, t &),**

Třída algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu member [hash_multiset:: swap](../standard-library/hash-multiset-class.md#swap) pro příklad, který používá verzi `swap`šablony.

## <a name="see-also"></a>Viz také:

[<hash_set>](../standard-library/hash-set.md)
