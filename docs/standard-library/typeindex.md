---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63eae51554003a2c12caf2522a912adc9b96ec02
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
