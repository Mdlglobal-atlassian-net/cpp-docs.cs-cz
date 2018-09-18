---
title: Chyba kompilátoru C2212 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2212
dev_langs:
- C++
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 773dff4c731830d300c97f1960b24923d2b7d67f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089876"
---
# <a name="compiler-error-c2212"></a>Chyba kompilátoru C2212

'identifier': možnost __based není dostupná pro ukazatele na funkce

Nelze použít deklaraci ukazatele na funkce `__based`. Pokud potřebujete data založená na kódu, použijte `__declspec` – klíčové slovo nebo `data_seg` direktivy pragma.