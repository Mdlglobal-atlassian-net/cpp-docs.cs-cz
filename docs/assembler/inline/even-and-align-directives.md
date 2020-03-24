---
title: Direktivy EVEN a ALIGN
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: b191ce0942d7596090bfd7948a37a5c9e6aac15e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169432"
---
# <a name="even-and-align-directives"></a>Direktivy EVEN a ALIGN

**Specifické pro společnost Microsoft**

I když vložený Assembler nepodporuje většinu direktiv MASM, podporuje `EVEN` a **Zarovnání**. Tyto direktivy obsahují instrukce **NOP** (bez operací) v kódu sestavení, jak je potřeba k zarovnání popisků na konkrétní hranice. Díky tomu jsou operace načítání instrukcí pro některé procesory efektivnější.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
