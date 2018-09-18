---
title: Chyba kompilátoru C3238 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3238
dev_langs:
- C++
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8fa0daec5e799e0ea661aa56d1a84604114ec7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090383"
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