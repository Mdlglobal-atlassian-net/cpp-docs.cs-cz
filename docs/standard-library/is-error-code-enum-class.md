---
title: is_error_code_enum – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: 4080c62034b224a9553eca2787aa1c2f2cf69ab8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454634"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum – třída

Představuje predikát typu, který testuje výčet [error_code](../standard-library/error-code-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
    class is_error_code_enum;
```

## <a name="remarks"></a>Poznámky

Instance tohoto predikátu [typu](../standard-library/type-traits.md) má hodnotu true, pokud typ `_Enum` je hodnota výčtu vhodná pro ukládání do objektu typu. `error_code`

Je povoleno přidat do tohoto typu specializace pro uživatelsky definované typy.

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
