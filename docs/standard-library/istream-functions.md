---
title: '&lt;funkce&gt; istreamu'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363070"
---
# <a name="ltistreamgt-functions"></a>&lt;funkce&gt; istreamu

|||
|-|-|
|[Swap](#istream_swap)|[ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>Swap

Vyměňuje prvky dvou objektů datového proudu.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Potok.

*Právo*\
Potok.

## <a name="ws"></a><a name="ws"></a>Ws

Přeskočí prázdné místo v datovém proudu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Potok.

### <a name="return-value"></a>Návratová hodnota

Proud.

### <a name="remarks"></a>Poznámky

Manipulátor extrahuje a `ch` vyhazuje všechny prvky, pro které [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype** \< **Elem**>:: **mezera**, **ch**) je pravdivá.

Funkce volá [setstate](../standard-library/basic-ios-class.md#setstate) **(eofbit),** pokud narazí na konec souboru při extrahování prvků. Vrátí *_Istr*.

### <a name="example"></a>Příklad

Příklad použití naleznete v `ws` [tématu>>operátoru](../standard-library/istream-operators.md#op_gt_gt) .

## <a name="see-also"></a>Viz také

[\<istream>](../standard-library/istream.md)
