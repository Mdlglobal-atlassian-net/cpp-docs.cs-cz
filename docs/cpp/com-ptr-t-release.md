---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170589"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Specifické pro společnost Microsoft**

Volá členskou funkci **Release** `IUnknown` na ukazatel zapouzdřeného rozhraní.

## <a name="syntax"></a>Syntaxe

```
void Release( );
```

## <a name="remarks"></a>Poznámky

Volá `IUnknown::Release` na ukazatel zapouzdřeného rozhraní a vyvolává chybu `E_POINTER`, pokud má ukazatel na rozhraní hodnotu NULL.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
