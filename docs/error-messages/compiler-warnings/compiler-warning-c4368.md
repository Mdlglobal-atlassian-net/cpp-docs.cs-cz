---
title: Upozornění kompilátoru C4368 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4368
dev_langs:
- C++
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52026f08a56faa1372b73b94fe91c96682510038
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073210"
---
# <a name="compiler-warning-c4368"></a>Upozornění kompilátoru C4368

nelze definovat 'člen' jako člen spravovaného 'typu': smíšené typy nejsou podporovány

Nativní datový člen nelze vložit do typu CLR.

Je však možné deklarovat ukazatel na nativní typ a řídit jeho dobu platnosti v konstruktoru, destruktoru a finalizační metodě spravované třídy. Další informace najdete v části [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Toto upozornění je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma k zakázání upozornění C4368.

## <a name="example"></a>Příklad

Následující ukázka generuje upozornění C4368.

```
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```