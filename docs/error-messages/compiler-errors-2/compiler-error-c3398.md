---
title: Chyba kompilátoru C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: f76515d58f020b414e6b79a7737463af80bd2d07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200811"
---
# <a name="compiler-error-c3398"></a>Chyba kompilátoru C3398

' operator ': nelze převést z ' function_signature ' na ' function_pointer '. Zdrojový výraz musí být symbol funkce.

Pokud [__clrcall](../../cpp/clrcall.md) konvence volání není určena při kompilaci s možností **/CLR**, kompilátor generuje dva vstupní body (adresy) pro každou funkci, nativní vstupní bod a spravovaný vstupní bod.

Ve výchozím nastavení kompilátor vrátí nativní vstupní bod, ale existují případy, kdy je spravovaný vstupní bod požadován (například při přiřazování adresy k ukazateli funkce `__clrcall`). Aby mohl kompilátor spolehlivě zvolit spravovaný vstupní bod v přiřazení, musí být pravá strana symbol funkce.
