---
title: Chyba kompilátoru C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: e4d52946126e7be6c6f2aef34b5eb5a93a0babad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187376"
---
# <a name="compiler-error-c3888"></a>Chyba kompilátoru C3888

"name": nepodporuje výraz const přidružený k tomuto datovému členu literálu C++vyhodnocovací

*Název* datový člen, který je deklarován s [literálu](../../extensions/literal-cpp-component-extensions.md) – klíčové slovo je inicializovat pomocí hodnoty kompilátor nepodporuje. Kompilátor podporuje pouze konstantní integral, enum nebo typy řetězců. Pravděpodobnou příčinou **C3888** chyby je, že datový člen je inicializován s polem bajtů.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte, že deklarovaný literální datový člen podporovaného typu.

## <a name="see-also"></a>Viz také:

[literal](../../extensions/literal-cpp-component-extensions.md)