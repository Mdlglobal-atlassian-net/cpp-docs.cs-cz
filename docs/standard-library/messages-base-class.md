---
title: messages_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: 79b6cb5f0b0c219e959f53fdc667f4c8af273cef
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451851"
---
# <a name="messagesbase-class"></a>messages_base – třída

Základní třída popisuje typ **int** pro katalog zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>Poznámky

Katalog typů je synonymum pro typ **int** , který popisuje možné návratové hodnoty ze zpráv:: [do_open](../standard-library/messages-class.md#do_open).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
