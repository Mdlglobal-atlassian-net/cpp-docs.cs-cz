---
title: Chyba kompilátoru C3398 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 336494ea9581289efd9a41e604a28984125ae61a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018129"
---
# <a name="compiler-error-c3398"></a>Chyba kompilátoru C3398

'operator': nelze převést z "function_signature" na "function_pointer". Zdrojový výraz musí být symbol funkce

Když [__clrcall](../../cpp/clrcall.md) konvence volání není specifikovat při kompilaci s **/CLR**, kompilátor generuje dva vstupní body (adresy) pro každou funkci, nativní vstupní bod a spravovaný vstupní bod.

Ve výchozím nastavení kompilátor vrací nativní vstupní bod, ale existují případy, kde je požadován spravovaný vstupní bod (například při přiřazování adres, které jsou `__clrcall` ukazatel na funkci). Aby kompilátor, aby spolehlivě zvolte spravovaný vstupní bod v přiřazení pravou stranu musí být symbol funkce.