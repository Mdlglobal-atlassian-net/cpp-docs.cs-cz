---
title: hash – struktura (standardní knihovna C++) | Microsoft Docs
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
ms.openlocfilehash: 6f2e9fdbef911a0160ff42925a9c7984f0211069
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="hash-structure-c-standard-library"></a>hash – struktura (standardní knihovna C++)

Definuje členské funkce, která vrátí hodnotu, která je jednoznačně dáno `Val`. Definuje – členská funkce [hash](../standard-library/hash-class.md) funkce, který je vhodný pro mapování hodnoty typu `thread::id` k distribučnímu index hodnot.

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

**Záhlaví:** \<vlákno >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<vlákno >](../standard-library/thread.md)<br/>
[unary_function – struktura](../standard-library/unary-function-struct.md)<br/>
