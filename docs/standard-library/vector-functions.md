---
title: '&lt;vektor&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: c93f535bb02cbaa1f688fba84f15d832381156c6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079311"
---
# <a name="ltvectorgt-functions"></a>&lt;vektor&gt; funkce

## <a name="swap"></a>  Prohození

Vymění prvky dvou vektorů.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Vektor poskytující prvky pro záměnu nebo vektor, jehož prvky mají být zaměněny vektoru *levé*.

*doleva*<br/>
Vektor, jehož prvky mají být zaměněny vektoru *správné*.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované na vektoru třídy kontejneru ke spuštění funkce člena `left`. [Vector::swap](../standard-library/vector-class.md) *(pravém*). Toto jsou instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony **šablony** \< **třída T**> **void prohození**( **T &**, **T &**), v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro členské funkce [vector::swap](../standard-library/vector-class.md) příklad, který používá verzi šablony `swap`.

## <a name="see-also"></a>Viz také:

[\<vektor >](../standard-library/vector.md)<br/>
