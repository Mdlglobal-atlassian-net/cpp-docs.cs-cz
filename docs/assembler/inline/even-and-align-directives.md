---
title: Direktivy EVEN a ALIGN | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06a1007c50e3490e5b14e4da886494557be0d37e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688298"
---
# <a name="even-and-align-directives"></a>Direktivy EVEN a ALIGN

**Specifické pro Microsoft**

I když vložený assembler nepodporuje většina direktivy MASM, podporuje `EVEN` a **ZAROVNAT**. Umístěte směrnic **NOP** (žádná operace) podle pokynů v kódu sestavení podle potřeby pro zarovnání popisků na určité hranice. Díky tomu operace načtení instrukce efektivnější pro některé procesory.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>