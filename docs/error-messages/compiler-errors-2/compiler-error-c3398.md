---
title: Chyba kompilátoru C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: 3b688012009a87c1e3d0db05e47133893daeaf34
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451061"
---
# <a name="compiler-error-c3398"></a>Chyba kompilátoru C3398

'operator': nelze převést z "function_signature" na "function_pointer". Zdrojový výraz musí být symbol funkce

Když [__clrcall](../../cpp/clrcall.md) konvence volání není specifikovat při kompilaci s **/CLR**, kompilátor generuje dva vstupní body (adresy) pro každou funkci, nativní vstupní bod a spravovaný vstupní bod.

Ve výchozím nastavení kompilátor vrací nativní vstupní bod, ale existují případy, kde je požadován spravovaný vstupní bod (například při přiřazování adres, které jsou `__clrcall` ukazatel na funkci). Aby kompilátor, aby spolehlivě zvolte spravovaný vstupní bod v přiřazení pravou stranu musí být symbol funkce.