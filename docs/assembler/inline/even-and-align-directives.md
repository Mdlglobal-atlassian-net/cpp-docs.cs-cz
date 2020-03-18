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
ms.openlocfilehash: 63fa73988b9b9433a988035789a923ac73936214
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441575"
---
# <a name="even-and-align-directives"></a>Direktivy EVEN a ALIGN

**Specifické pro společnost Microsoft**

I když vložený Assembler nepodporuje většinu direktiv MASM, podporuje `EVEN` a **Zarovnání**. Tyto direktivy obsahují instrukce **NOP** (bez operací) v kódu sestavení, jak je potřeba k zarovnání popisků na konkrétní hranice. Díky tomu jsou operace načítání instrukcí pro některé procesory efektivnější.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>