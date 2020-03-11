---
title: '&lt;nastavení&gt; funkcí'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875760"
---
# <a name="ltsetgt-functions"></a>&lt;nastavení&gt; funkcí

## <a name="swap"></a>swap (map)

Vymění prvky dvou sad.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Sada poskytující prvky, které mají být zaměněny, nebo sadu, jejíž prvky mají být vyměňovány pomocí těch, které jsou nastaveny *vlevo*.

*levý*\
Sada, jejíž prvky mají být vyměňovány s nastavením *práva*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru nastavenou na spouštění členské funkce `left.`[swap](../standard-library/set-class.md#swap)(`right`). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony

`template` \< **třídy**> **void swap**( **t &** , **t &** )

Třída algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

Viz příklad kódu pro sadu tříd členů [:: swap](../standard-library/set-class.md#swap) pro příklad použití verze šablony `swap`.

## <a name="swap_multiset"></a>swap (multiset)

Vyměňuje prvky dvou množin.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Multiset poskytuje prvky, které mají být měněny, nebo multiset, jejichž prvky mají být vyměňovány s multiset *doleva*.

*levý*\
Multiset, jehož prvky mají být vyměňovány pomocí multiset *práva*.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru multiset ke spuštění členské funkce `left.`[swap](../standard-library/multiset-class.md#swap)(`right`). Toto je instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony

`template` \< **třídy**> **void swap**( **t &** , **t &** )

Třída algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

### <a name="example"></a>Příklad

V příkladu kódu pro třídu member [multiset:: swap](../standard-library/multiset-class.md#swap)najdete příklad použití verze šablony `swap`.
