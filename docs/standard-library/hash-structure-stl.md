---
title: hash – struktura (standardní knihovna C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6f00b3c3136a4a2df96667d0f99f195339c60f1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056617"
---
# <a name="hash-structure-c-standard-library"></a>hash – struktura (standardní knihovna C++)

Definuje členskou funkci, která vrací hodnotu, která jednoznačně určuje `Val`. Definuje členskou funkci [hash](../standard-library/hash-class.md) funkce, která je vhodná pro mapování hodnot typu `thread::id` k distribuci hodnot indexu.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vlákna >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<vlákna >](../standard-library/thread.md)<br/>
[unary_function – struktura](../standard-library/unary-function-struct.md)<br/>
