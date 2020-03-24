---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 51182b461aeac83c12bb18a573a49b2d4347a190
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189923"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Specifické pro společnost Microsoft**

Volá `AddRef` členskou funkci `IUnknown` na ukazatel zapouzdřeného rozhraní.

## <a name="syntax"></a>Syntaxe

```
void AddRef( );
```

## <a name="remarks"></a>Poznámky

Volá `IUnknown::AddRef` na ukazatel zapouzdřeného rozhraní a vyvolává chybu `E_POINTER`, pokud má ukazatel hodnotu NULL.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
