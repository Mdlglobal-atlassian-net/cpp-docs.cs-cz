---
title: "&lt;alokátorů&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs: C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 986d972bdc778ddd47c2c0098955f2b570c881ce
ms.sourcegitcommit: a7e4956c1150273e8dd39fda8b41655a6cf2cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2017
---
# <a name="ltallocatorsgt-operators"></a>&lt;alokátorů&gt; operátory

Toto jsou globální šablona funkce operátor definované v &lt;alokátorů&gt;. Členské funkce operátor třídy najdete v dokumentaci třídy.

|||
|-|-|
|[operator!=](#op_neq)|[Operator ==](#op_eq_eq)|

##  <a name="op_neq"></a>Operator! =

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

##  <a name="op_eq_eq"></a>Operator ==

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

[\<alokátorů >](../standard-library/allocators-header.md)  
