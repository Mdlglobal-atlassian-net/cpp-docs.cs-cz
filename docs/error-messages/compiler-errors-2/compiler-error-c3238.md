---
title: Chyba kompilátoru C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: d81fd0fb3612a8c22fa6365aa7fc6dddb89cf120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481156"
---
# <a name="compiler-error-c3238"></a>Chyba kompilátoru C3238

'type': typ s tímto názvem již byl přemístěn do sestavení 'assembly'

Typ byl definován v klientské aplikaci, která je také definován pomocí typu předávání syntaxe v odkazovaném sestavení. Oba typy nemůže být definován v oboru aplikace.

Zobrazit [předávání typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md) Další informace.

## <a name="example"></a>Příklad

Tímto vzorovým kódem se vytvoří sestavení obsahující typ, který byl předán z jiného sestavení.

```
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Příklad

Následující příklad vytvoří sestavení, který se používá pro jiné definice typu, ale obsahuje nejen posloupnosti syntaxi typů.

```
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3238.

```
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```