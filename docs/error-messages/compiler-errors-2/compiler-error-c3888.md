---
title: Chyba kompilátoru C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 067412e59041cb98b68cb373c4671c243ab8a0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479063"
---
# <a name="compiler-error-c3888"></a>Chyba kompilátoru C3888

"name": nepodporuje výraz const přidružený k tomuto datovému členu literálu C + +/ CLI

*Název* datový člen, který je deklarován s [literálu](../../windows/literal-cpp-component-extensions.md) – klíčové slovo je inicializovat pomocí hodnoty kompilátor nepodporuje. Kompilátor podporuje pouze konstantní integral, enum nebo typy řetězců. Pravděpodobnou příčinou **C3888** chyby je, že datový člen je inicializován s polem bajtů.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte, že deklarovaný literální datový člen podporovaného typu.

## <a name="see-also"></a>Viz také

[literál](../../windows/literal-cpp-component-extensions.md)