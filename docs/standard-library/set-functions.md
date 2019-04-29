---
title: '&lt;Nastavte&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: 3873a85218c738b3a9693926e064a10b82a553c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412615"
---
# <a name="ltsetgt-functions"></a>&lt;Nastavte&gt; funkce

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

*doprava*<br/>
Sada poskytující prvky pro záměnu nebo set, jehož prvky mají být zaměněny sady *levé*.

*doleva*<br/>
Sada, jehož prvky mají být zaměněny sady *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na nastavení ke spuštění funkce člena třídy kontejneru `left.` [prohození](../standard-library/set-class.md#swap)(`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablon

`template` \< **classT**> **void prohození**( **T &**, **T &**)

Třída v algoritmu funguje tak, že přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro člen třídy [set::swap](../standard-library/set-class.md#swap) příklad použití šablony verze `swap`.

## <a name="swap_multiset"></a>  swap (multiset)

Vymění prvky dvou multisets.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Multiset poskytující prvky pro záměnu nebo multiset, jehož prvky mají vyměnit s těmi třída multiset *levé*.

*doleva*<br/>
Multiset, jehož prvky mají vyměnit s těmi třída multiset *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na třída multiset kontejneru ke spuštění funkce člena `left.` [prohození](../standard-library/multiset-class.md#swap)(`right`). Toto je instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablon

`template` \< **classT**> **void prohození**( **T &**, **T &**)

Třída v algoritmu funguje tak, že přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro člen třídy [multiset::swap](../standard-library/multiset-class.md#swap)příklad použití šablony verze `swap`.

## <a name="see-also"></a>Viz také:

[\<set>](../standard-library/set.md)<br/>
