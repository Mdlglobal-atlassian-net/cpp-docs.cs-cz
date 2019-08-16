---
title: Chyba kompilátoru C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 98b5bf0a1315236f3ce96fd4b8c140ce1ab70a9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501039"
---
# <a name="compiler-error-c2778"></a>Chyba kompilátoru C2778

nesprávně vytvořený identifikátor GUID v __declspec (UUID ())

Rozšířenému atributu [UUID](../../cpp/uuid-cpp.md) je zadán nesprávný identifikátor GUID.

Identifikátor GUID musí být řetězec hexadecimálních čísel v následujícím formátu:

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

Rozšířený atribut přijímá řetězce rozpoznané v CLSIDFromString s oddělovači nebo bez závorek. [](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring) `uuid`

Následující ukázka generuje C2778:

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```