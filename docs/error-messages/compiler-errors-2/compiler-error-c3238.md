---
title: Chyba kompilátoru C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: d70bb6dac7cb43701b57f3821872e02ab31426dc
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775619"
---
# <a name="compiler-error-c3238"></a>Chyba kompilátoru C3238

'type': typ s tímto názvem již byl přemístěn do sestavení 'assembly'

Typ byl definován v klientské aplikaci, která je také definován pomocí typu předávání syntaxe v odkazovaném sestavení. Oba typy nemůže být definován v oboru aplikace.

Zobrazit [předávání typu (C + +/ CLI)](../../extensions/type-forwarding-cpp-cli.md) Další informace.

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