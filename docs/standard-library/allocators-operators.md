---
title: '&lt;alokátory&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430261"
---
# <a name="ltallocatorsgt-operators"></a>&lt;alokátory&gt; operátory

Toto jsou globální šablona operátoru funkce definované v &lt;alokátorů&gt;. Třída členské funkce operátora najdete v dokumentaci třídy.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

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
|*doleva*|Jeden z allocator objekty, které chcete otestovat nerovnost.|
|*doprava*|Jeden z allocator objekty, které chcete otestovat nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekty přidělování nejsou stejné; **false** Pokud allocator objekty rovnají.

### <a name="remarks"></a>Poznámky

Vrátí operátor šablony `!(left == right)`.

## <a name="op_eq_eq"></a>  Operator ==

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
|*doleva*|Jeden z allocator objekty, které chcete být testovány z hlediska rovnosti.|
|*doprava*|Jeden z allocator objekty, které chcete být testovány z hlediska rovnosti.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud allocator objekty rovnají. **false** Pokud objekty přidělování nejsou stejné.

### <a name="remarks"></a>Poznámky

Tato šablona operátor vrátí `left.equals(right)`.

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)
