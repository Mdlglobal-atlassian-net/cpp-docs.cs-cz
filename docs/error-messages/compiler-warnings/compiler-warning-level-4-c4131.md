---
title: Upozornění (úroveň 4) C4131 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4131
dev_langs:
- C++
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43de917b2a6aff38602a6118e599c0d9df262a70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033183"
---
# <a name="compiler-warning-level-4-c4131"></a>Kompilátor upozornění (úroveň 4) C4131

'function': používá deklarátor starého stylu

Deklarace zadaná funkce není v podobě prototypu.

Deklarace funkcí starého typu mají být převedeny do formuláře prototypu.

Následující příklad ukazuje deklaraci funkce starého typu:

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

Následující příklad zobrazí formulář prototyp:

```
void addrec( char *name, int id )
{ }
```