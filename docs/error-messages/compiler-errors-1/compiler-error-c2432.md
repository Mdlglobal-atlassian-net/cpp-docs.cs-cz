---
title: Chyba kompilátoru C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: e2983d966a6290ce19713c63feb502c8ffc74bf1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166838"
---
# <a name="compiler-error-c2432"></a>Chyba kompilátoru C2432

Neplatný odkaz na 16bitová data v 'identifier'

Registr 16 bitů se používá jako index nebo základní registrace. Kompilátor nepodporuje odkazování na 16bitová data. 16bitové registrů nelze použít jako index nebo základní registrů při kompilaci pro 32bitového kódu.

Následující ukázka generuje C2432:

```
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```