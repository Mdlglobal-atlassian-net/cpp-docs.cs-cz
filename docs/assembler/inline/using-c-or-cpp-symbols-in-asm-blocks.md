---
title: Použití jazyka C nebo C++ symboly v blocích __asm | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ba8426e2a7ae1152a41fafa0c239498801c6e4d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678890"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Používání symbolů jazyka C nebo C++ v blocích __asm

**Specifické pro Microsoft**

`__asm` Bloku mohou odkazovat na jakýkoli symbol jazyka C nebo C++ v oboru, ve kterém se zobrazí bloku. (Symboly C a C++ jsou názvy proměnných, funkce názvy a popisky, které je, názvy, které nejsou Symbolické konstanty nebo `enum` členy. Nelze volat C++ členské funkce.)

Používání symbolů jazyka C a C++ platí několik omezení:

- Každý příkaz symbolického jazyka může obsahovat pouze jeden C nebo C++ symbol. Více symbolů se může objevit v stejné instrukci sestavení jenom s **délka**, **typ**, a **velikost** výrazy.

- Funkce odkazované v `__asm` bloku musí být deklarovány dříve v programu (prototypem). V opačném případě kompilátor nelze rozlišit názvy a popisky v `__asm` bloku.

- `__asm` Block nemůže používat žádné symboly jazyka C nebo C++ se stejnou pravopis MASM vyhrazená slova (bez ohledu na malá). MASM vyhrazená slova instrukcí názvy patří například **PUSH** a názvy, například SI zaregistrujte.

- Značky struktury a sjednocení nejsou rozpoznány v `__asm` bloky.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>