---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393906"
---
# <a name="virtual-c"></a>virtual (C++)

**Virtuální** – klíčové slovo deklaruje virtuální funkci nebo virtuální základní třídy.

## <a name="syntax"></a>Syntaxe

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Parametry

*specifikátory typu*<br/>
Určuje návratový typ virtuální členské funkce.

*member-function-declarator*<br/>
Deklaruje členskou funkci.

*access-specifier*<br/>
Definuje úroveň přístupu na základní třídu **veřejné**, **chráněné** nebo **privátní**. Před nebo po ní se může objevit **virtuální** – klíčové slovo.

*base-class-name*<br/>
Identifikuje dříve deklarovaný typ třídy.

## <a name="remarks"></a>Poznámky

Zobrazit [virtuální funkce](../cpp/virtual-functions.md) Další informace.

Viz také následující klíčová slova: [třídy](../cpp/class-cpp.md), [privátní](../cpp/private-cpp.md), [veřejné](../cpp/public-cpp.md), a [chráněné](../cpp/protected-cpp.md).

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)