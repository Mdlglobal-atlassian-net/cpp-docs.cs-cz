---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663356"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Specifické pro Microsoft**

Volání `AddRef` členskou funkci `IUnknown` na zapouzdřený ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```
void AddRef( );
```

## <a name="remarks"></a>Poznámky

Volání `IUnknown::AddRef` na zapouzdřený ukazatel rozhraní, vyvolání `E_POINTER` chyby, pokud je ukazatel NULL.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)