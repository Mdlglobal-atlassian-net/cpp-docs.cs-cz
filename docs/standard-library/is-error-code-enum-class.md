---
title: is_error_code_enum – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: d890eb6a1b7c93f9ae5b87018c3bf1d6eeae8abb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336477"
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

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
