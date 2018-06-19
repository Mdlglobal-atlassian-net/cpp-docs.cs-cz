---
title: is_error_code_enum – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7024817c5a02d7c4a529167ca65a292b34be119
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844598"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum – třída

Představuje predikátem typu, který vyhledá [error_code](../standard-library/error-code-class.md) výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
class is_error_code_enum;
```

## <a name="remarks"></a>Poznámky

Instanci tohoto objektu [predikátem typu](../standard-library/type-traits.md) blokování hodnota true, pokud typ `_Enum` je vhodný pro ukládání do objektu typu hodnota výčtu `error_code`.

Je přípustné, chcete-li přidat specializací na tento typ pro uživatelem definované typy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error – >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
