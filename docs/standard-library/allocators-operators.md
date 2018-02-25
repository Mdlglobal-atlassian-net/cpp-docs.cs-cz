---
title: "&lt;alokátorů&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: e84f3c66adaf4d4d0cd5af68ee51841025bd89b2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltallocatorsgt-operators"></a>&lt;alokátorů&gt; operátory

Toto jsou globální šablona funkce operátor definované v &lt;alokátorů&gt;. Členské funkce operátor třídy najdete v dokumentaci třídy.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

##  <a name="op_neq"></a>  Operator! =

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
|`left`|Jeden z objektů allocator má být testována nerovnost.|
|`right`|Jeden z objektů allocator má být testována nerovnost.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud allocator objekty nejsou stejné; **false** Pokud allocator objekty jsou stejné.

### <a name="remarks"></a>Poznámky

Vrátí operátor šablony `!(left == right)`.

##  <a name="op_eq_eq"></a>  Operator ==

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
|`left`|Jeden z objektů allocator má být testována rovnosti.|
|`right`|Jeden z objektů allocator má být testována rovnosti.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud allocator objekty jsou stejné; **false** Pokud allocator objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Tento operátor šablony vrátí `left.equals(right)`.

## <a name="see-also"></a>Viz také

[\<allocators>](../standard-library/allocators-header.md)  
