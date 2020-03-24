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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169575"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C++ v sestavení inline assemblerem

**Specifické pro společnost Microsoft**

Blok `__asm` může volat pouze globální C++ funkce, které nejsou přetíženy. Pokud voláte přetíženou globální C++ funkci nebo C++ členskou funkci, vyvolá kompilátor chybu.

Můžete také volat všechny funkce deklarované s **externím propojením "C"** . To umožňuje, aby blok `__asm` v C++ rámci programu volal funkce knihovny jazyka C, protože všechny standardní hlavičkové soubory deklaruje funkce knihovny pro externí propojení **"C"** .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
