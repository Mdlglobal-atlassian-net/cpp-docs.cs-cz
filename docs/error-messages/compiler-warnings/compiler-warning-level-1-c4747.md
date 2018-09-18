---
title: Upozornění (úroveň 1) C4747 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d3eb5b83fedc7455cbf1b97119296a6eb6a1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118476"
---
# <a name="compiler-warning-level-1-c4747"></a>Kompilátor upozornění (úroveň 1) C4747

Volání spravované 'entrypoint': nastavený zámek zavaděče, včetně vstupního bodu DLL a volání dosáhlo ze vstupního bodu DLL se možná nespustí spravovaný kód

Kompilátor najít (o) vstupní bod knihovny DLL zkompilované na MSIL.  Z důvodu možných problémů při načítání knihovny DLL, jehož vstupního bodu byla zkompilována do jazyka MSIL se důrazně nedoporučuje v kompilaci funkci vstupního bodu DLL do jazyka MSIL.

Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md) a [chyba Linkerů LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Modul s parametrem se nekompilují **/CLR**.

1. Označit funkci vstupního bodu pomocí `#pragma unmanaged`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4747.

```
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```