---
title: Závažná chyba C1197 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58561e7bd906fc750779ef53a4f68ec27088a3b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024759"
---
# <a name="fatal-error-c1197"></a>Závažná chyba C1197

nemůže odkazovat 'mscorlib.dll_1', protože program už odkazuje na "mscorlib.dll_2"

Kompilátor odpovídá verzi modulu common language runtime.  Však byl proveden pokus o tak, aby odkazovaly na verzi common soubor modulu runtime jazyka z předchozí verze.

Chcete-li vyřešit tuto chybu, odkazovat pouze na soubory z verze common language runtime, dodávané s verzí jazyka Visual C++, který je aktuálně kompilován s.

## <a name="example"></a>Příklad

Následující ukázka generuje C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```