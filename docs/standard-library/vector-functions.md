---
title: '&lt;vektor&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: dbcb2524736bcb99693f3a4b27790c3447d58fe3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltvectorgt-functions"></a>&lt;vektor&gt; funkce


## <a name="swap"></a>  Swap

Výměny elementy dvěma způsoby.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Vektor poskytování elementy pro si místo nebo vektoru, jehož elementy jsou k výměně s těmi, která vektoru `left`.

`left` Vektor, jehož elementy jsou k výměně s těmi, která vektoru `right`.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializuje na vektoru třída kontejneru provést – členská funkce `left`. [Vector::swap](../standard-library/vector-class.md) *(vpravo*). Toto jsou instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony **šablony** \< **třída T**> **void swap**( **T &**, **T &**), v algoritmu třídy funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad kódu pro funkce člen [vector::swap](../standard-library/vector-class.md) pro příklad, který používá verzi šablony služby `swap`.

## <a name="see-also"></a>Viz také

[\<vektor >](../standard-library/vector.md)<br/>
