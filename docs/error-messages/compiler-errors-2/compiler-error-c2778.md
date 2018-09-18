---
title: Chyba kompilátoru C2778 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2778
dev_langs:
- C++
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6106832ea82531a6f6915417ac56d53504db882e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022159"
---
# <a name="compiler-error-c2778"></a>Chyba kompilátoru C2778

nesprávně vytvořené GUID v: __declspec(uuid())

Je předán nesprávný identifikátor GUID [uuid](../../cpp/uuid-cpp.md) rozšířeného atributu.

Identifikátor GUID musí být řetězec šestnáctkových čísel v následujícím formátu:

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

`uuid` Přijímá rozšířený atribut řetězců rozpoznávaných [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring), s oddělovači nebo bez závorek.

Následující ukázka generuje C2778:

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```