---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 189fb7cd3757a3f71a50badc682b7b4db611b4e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855107"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

Zahrnují standardní hlavičku \<typeindex > Chcete-li definovat třídy a funkce, které podporují indexování objekty třídy [type_info](../cpp/type-info-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <typeindex>
```

## <a name="remarks"></a>Poznámky

[Hash – struktura](../standard-library/hash-structure.md) definuje `hash function` který je vhodný pro mapování hodnoty typu [type_index](../standard-library/type-index-class.md) k distribučnímu index hodnot.

`type_index` Třída zabalí ukazatel na `type_info` objekt, který má být užitečné při indexování.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
