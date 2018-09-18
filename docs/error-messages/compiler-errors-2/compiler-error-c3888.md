---
title: Chyba kompilátoru C3888 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9292f54fee467a5f8d01202b6ed7ca991b52d43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096454"
---
# <a name="compiler-error-c3888"></a>Chyba kompilátoru C3888

"name": nepodporuje výraz const přidružený k tomuto datovému členu literálu C + +/ CLI

*Název* datový člen, který je deklarován s [literálu](../../windows/literal-cpp-component-extensions.md) – klíčové slovo je inicializovat pomocí hodnoty kompilátor nepodporuje. Kompilátor podporuje pouze konstantní integral, enum nebo typy řetězců. Pravděpodobnou příčinou **C3888** chyby je, že datový člen je inicializován s polem bajtů.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte, že deklarovaný literální datový člen podporovaného typu.

## <a name="see-also"></a>Viz také

[literál](../../windows/literal-cpp-component-extensions.md)