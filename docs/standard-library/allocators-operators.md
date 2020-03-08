---
title: '&lt;přidělování&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875955"
---
# <a name="ltallocatorsgt-operators"></a>&lt;přidělování&gt; operátory

Jedná se o funkce operátoru globálních šablon definované v&gt;&lt;přidělování. Funkce operátoru členů třídy naleznete v dokumentaci třídy.

|||
|-|-|
|[operator!=](#op_neq)|[operator = = – operátor](#op_eq_eq)|

## <a name="op_neq"></a>! = – operátor

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
|*zbývá*|Jeden z objektů přidělování, který má být testován na nerovnost.|
|*Kliknutím*|Jeden z objektů přidělování, který má být testován na nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekty přidělování nejsou stejné; **false** , pokud jsou objekty přidělování stejné.

### <a name="remarks"></a>Poznámky

Operátor šablony vrací `!(left == right)`.

## <a name="op_eq_eq"></a>operator = = – operátor

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
|*zbývá*|Jeden z objektů přidělování, který má být testován pro rovnost.|
|*Kliknutím*|Jeden z objektů přidělování, který má být testován pro rovnost.|

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou objekty přidělování stejné; **false** , pokud objekty přidělování nejsou stejné.

### <a name="remarks"></a>Poznámky

Tento operátor šablony vrací `left.equals(right)`.

## <a name="see-also"></a>Viz také

[\<přidělování >](../standard-library/allocators-header.md)
