---
title: _com_ptr_t::GetInterfacePtr
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetInterfacePtr
helpviewer_keywords:
- GetInterfacePtr method [C++]
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
ms.openlocfilehash: f3244d59159855ff4060c944874e859cb5ec23ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170732"
---
# <a name="_com_ptr_tgetinterfaceptr"></a>_com_ptr_t::GetInterfacePtr

**Specifické pro společnost Microsoft**

Vrátí zapouzdřený ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```
Interface* GetInterfacePtr( ) const throw( );
Interface*& GetInterfacePtr() throw();
```

## <a name="remarks"></a>Poznámky

Vrátí zapouzdřený ukazatel rozhraní, který může mít hodnotu NULL.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
