---
title: underlying_type – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b3f796d5039900b591c219c840d1aef94d23e8f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957578"
---
# <a name="underlyingtype-class"></a>underlying_type – třída

Vytvoří základní celočíselného typu pro typ výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parametry

*T*  
 Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

`type` Definice typu člena třídy šablony názvů základního celočíselného typu *T*, když *T* je číselného typu, jinak neexistuje žádný člen typedef `type`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
