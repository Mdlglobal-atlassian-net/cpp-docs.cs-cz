---
title: is_error_condition_enum – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: c40f8f6eb93a33098cfbcf8133f08c56285abb43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452605"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum – třída

Představuje predikát typu, který testuje výčet [error_condition](../standard-library/error-condition-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>Poznámky

Instance tohoto predikátu [typu](../standard-library/type-traits.md) má hodnotu true, pokud typ `_Enum` je hodnota výčtu vhodná pro ukládání do objektu typu. `error_condition`

Je povoleno přidat do tohoto typu specializace pro uživatelsky definované typy.

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
