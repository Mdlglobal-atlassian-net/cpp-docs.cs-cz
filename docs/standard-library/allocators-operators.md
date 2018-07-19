---
title: '&lt;alokátory&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 0bc4ce7c36d3ba097b04b1704fea7633eb7d26ea
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962953"
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
