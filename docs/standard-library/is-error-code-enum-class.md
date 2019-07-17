---
title: is_error_code_enum – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: bc4ed7cd2e058414448c9366011b9efab97ee3d5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245193"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum – třída

Představuje typ predikát, který testuje [error_code](../standard-library/error-code-class.md) výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
    class is_error_code_enum;
```

## <a name="remarks"></a>Poznámky

Instanci tohoto objektu [predikát typu](../standard-library/type-traits.md) obsahuje hodnotu true, pokud typ `_Enum` je vhodná pro ukládání v objektu typu hodnoty výčtu `error_code`.

Je přípustné, chcete-li přidat specializace k tomuto typu pro typy definované uživatelem.

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
