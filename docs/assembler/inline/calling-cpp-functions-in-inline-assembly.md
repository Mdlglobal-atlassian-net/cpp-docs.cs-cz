---
title: Volání funkcí jazyka C++ ve vloženém sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4717ae24dc1a0b6f51f7a00f68f6569c2f988c65
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678941"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C++ v sestavení inline assemblerem

**Specifické pro Microsoft**

`__asm` Bloku může volat pouze globální funkcí jazyka C++, které nejsou přetíženy. Při volání přetížené funkce C++ globální nebo členské funkce C++, kompilátor vyvolá chybu.

Můžete také volat jakékoli funkce deklarované s **extern "C"** propojení. To umožňuje `__asm` blok v rámci programu v jazyce C++ pro volání funkce knihovny jazyka C, protože všechny soubory standardní hlavičku deklarace funkcí knihovny, které mají mít **extern "C"** propojení.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>