---
title: Upozornění (úroveň 4) C4611 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 723976dc8b7085ede9b3157445ff3026de6fc4b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091046"
---
# <a name="compiler-warning-level-4-c4611"></a>Kompilátor upozornění (úroveň 4) C4611

interakce mezi 'function' a destrukcí objektu C++ není typu portable.

Na některých platformách, funkce, které zahrnují **catch** nemusí podporovat sémantiku objektu C++ odstranění, když jsou mimo rozsah.

Abyste zabránili neočekávanému chování, vyhněte se použití **catch** ve funkcích, které mají konstruktory a destruktory.

Se objeví toto upozornění jen jednou; Zobrazit [– Direktiva pragma upozornění](../../preprocessor/warning.md).