---
title: Volání funkcí jazyka C++ v sestavení inline assemblerem
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 666f7b2a59f0d48a14be54a439b6402f2a4d3128
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458220"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C++ v sestavení inline assemblerem

**Specifické pro Microsoft**

`__asm` Bloku může volat pouze globální funkcí jazyka C++, které nejsou přetíženy. Při volání přetížené funkce C++ globální nebo členské funkce C++, kompilátor vyvolá chybu.

Můžete také volat jakékoli funkce deklarované s **extern "C"** propojení. To umožňuje `__asm` blok v rámci programu v jazyce C++ pro volání funkce knihovny jazyka C, protože všechny soubory standardní hlavičku deklarace funkcí knihovny, které mají mít **extern "C"** propojení.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>