---
title: virtuální (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2471dac12db574aa045142a654effafadbabd732
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092262"
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

*deklarátor členské funkce*<br/>
Deklaruje členskou funkci.

*specifikátor přístupu*<br/>
Definuje úroveň přístupu na základní třídu **veřejné**, **chráněné** nebo **privátní**. Před nebo po ní se může objevit **virtuální** – klíčové slovo.

*Název třídy Base*<br/>
Identifikuje dříve deklarovaný typ třídy.

## <a name="remarks"></a>Poznámky

Zobrazit [virtuální funkce](../cpp/virtual-functions.md) Další informace.

Viz také následující klíčová slova: [třídy](../cpp/class-cpp.md), [privátní](../cpp/private-cpp.md), [veřejné](../cpp/public-cpp.md), a [chráněné](../cpp/protected-cpp.md).

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)