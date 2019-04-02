---
title: Chyba kompilátoru C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 20251292ec4635ea855a56890878bc55f567ab62
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777464"
---
# <a name="compiler-error-c3888"></a>Chyba kompilátoru C3888

"name": nepodporuje výraz const přidružený k tomuto datovému členu literálu C + +/ CLI

*Název* datový člen, který je deklarován s [literálu](../../extensions/literal-cpp-component-extensions.md) – klíčové slovo je inicializovat pomocí hodnoty kompilátor nepodporuje. Kompilátor podporuje pouze konstantní integral, enum nebo typy řetězců. Pravděpodobnou příčinou **C3888** chyby je, že datový člen je inicializován s polem bajtů.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte, že deklarovaný literální datový člen podporovaného typu.

## <a name="see-also"></a>Viz také

[literál](../../extensions/literal-cpp-component-extensions.md)