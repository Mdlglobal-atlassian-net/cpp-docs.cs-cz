---
title: Chyba kompilátoru C2142 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2142
dev_langs:
- C++
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32301087ac1f06f1958ca8de7d2f66645dafb3d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032488"
---
# <a name="compiler-error-c2142"></a>Chyba kompilátoru C2142

deklarace funkce se liší, parametry proměnné jsou zadané jenom v jednom z nich

Jedna deklarace funkce obsahuje seznam parametrů proměnných. Další deklarace je nepodporuje. ANSI jazyka C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) pouze.

Následující ukázka generuje C2142:

```
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```