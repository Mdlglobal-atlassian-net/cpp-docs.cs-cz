---
title: Chyba kompilátoru C3384 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3384
dev_langs:
- C++
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75c904556951838de0308aea499980132440cbdb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061601"
---
# <a name="compiler-error-c3384"></a>Chyba kompilátoru C3384

'type_parameter': omezení value a omezení ref se vzájemně vylučují

Nelze omezit obecného typu pro obě `value class` a `ref class`.

Zobrazit [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3384.

```
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```