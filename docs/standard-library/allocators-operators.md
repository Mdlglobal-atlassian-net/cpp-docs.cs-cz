---
title: '&lt;operátory&gt; přidělování'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7bc37e98ed85582cac8fc7ae21e54a6d5da9e06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364965"
---
# <a name="ltallocatorsgt-operators"></a>&lt;operátory&gt; přidělování

Jedná se o funkce operátoru globální šablony definované v &lt;alokátory&gt;. Funkce operátoru člena třídy naleznete v dokumentaci ke třídě.

|||
|-|-|
|[operátor!=](#op_neq)|[operátor==](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>operátor!=

Testy pro nerovnost mezi objekty přidělování z dané třídy.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Vlevo*|Jeden z objektů alokátoru, které mají být testovány na nerovnost.|
|*Právo*|Jeden z objektů alokátoru, které mají být testovány na nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**true,** pokud alokátor objekty nejsou stejné; **false,** pokud alokátor objekty jsou stejné.

### <a name="remarks"></a>Poznámky

Operátor šablony `!(left == right)`vrátí .

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

Testy pro rovnost mezi objekty přidělování z dané třídy.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Vlevo*|Jeden z objektů alokátoru, které mají být testovány na rovnost.|
|*Právo*|Jeden z objektů alokátoru, které mají být testovány na rovnost.|

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou alokátorové objekty stejné; **false,** pokud alokátor objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Tento operátor `left.equals(right)`šablony vrátí .

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
