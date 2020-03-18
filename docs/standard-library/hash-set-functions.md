---
title: '&lt;hash_set&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 2fbc05c16ba6629397bbb07bab30cb9315a16e1f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421616"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; funkce

|||
|-|-|
|[adresu](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>adresu

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_set třídy](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Hash_set poskytují prvky, které mají být měněny, nebo hash_set jejichž prvky mají být vyměňovány pomocí těch hash_set *doleva*.

*levý*\
Hash_set, jejichž prvky mají být vyměněny pomocí hash_set *právo*.

### <a name="remarks"></a>Poznámky

Funkce šablony `swap` je algoritmus specializovaný na třídu kontejneru hash_set ke spuštění členské funkce `left.`[swap](../standard-library/hash-set-class.md#swap)(`right`). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony

**Template \<třída T > void swap (T &, T &),**

Třída algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu member [hash_set:: swap](../standard-library/hash-set-class.md#swap) pro příklad, který používá šablonu verze `swap`.

## <a name="swap_hash_multiset"></a>swap (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_set třídy](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Hash_multiset poskytují prvky, které mají být měněny, nebo hash_multiset jejichž prvky mají být vyměňovány pomocí těch hash_multiset *doleva*.

*levý*\
Hash_multiset, jejichž prvky mají být vyměněny pomocí hash_multiset *právo*.

### <a name="remarks"></a>Poznámky

Funkce šablony `swap` je algoritmus specializovaný na třídu kontejneru hash_multiset ke spuštění členské funkce `left.`[swap](../standard-library/hash-multiset-class.md#swap)(`right`). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony

**Template \<třída T > void swap (T &, T &),**

Třída algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro třídu member [hash_multiset:: swap](../standard-library/hash-multiset-class.md#swap) pro příklad, který používá šablonu verze `swap`.

## <a name="see-also"></a>Viz také

[<hash_set>](../standard-library/hash-set.md)
