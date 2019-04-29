---
title: _com_ptr_t::GetInterfacePtr
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetInterfacePtr
helpviewer_keywords:
- GetInterfacePtr method [C++]
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
ms.openlocfilehash: dba5b5e2fcebf87ef196e2f33adedf88cc42b559
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399301"
---
# <a name="comptrtgetinterfaceptr"></a>_com_ptr_t::GetInterfacePtr

**Microsoft Specific**

Vrátí zapouzdřený ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```
Interface* GetInterfacePtr( ) const throw( );
Interface*& GetInterfacePtr() throw();
```

## <a name="remarks"></a>Poznámky

Vrátí zapouzdřený ukazatel rozhraní, což může mít hodnotu NULL.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)