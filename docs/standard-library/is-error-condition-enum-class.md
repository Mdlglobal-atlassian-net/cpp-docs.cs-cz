---
title: is_error_condition_enum – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 1b5b55431db806bb109a58199ad9d2d7c16f38ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62162431"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum – třída

Představuje typ predikát, který testuje [error_condition –](../standard-library/error-condition-class.md) výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
class is_error_condition_enum;
```

## <a name="remarks"></a>Poznámky

Instanci tohoto objektu [predikát typu](../standard-library/type-traits.md) obsahuje hodnotu true, pokud typ `_Enum` je vhodná pro ukládání v objektu typu hodnoty výčtu `error_condition`.

Je přípustné, chcete-li přidat specializace k tomuto typu pro typy definované uživatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
