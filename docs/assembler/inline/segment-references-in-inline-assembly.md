---
title: Odkazy na segmenty ve vloženém sestavení
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 5c07fa897da23a55f376a20e7588c8c8c269d1a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577330"
---
# <a name="segment-references-in-inline-assembly"></a>Odkazy na segmenty ve vloženém sestavení

**Specifické pro Microsoft**

Musíte odkazovat na segmentů podle registru, nikoli podle názvu (název segmentu `_TEXT` je neplatný, například). Přepsání segmentu používaly registru explicitně, stejně jako v ES: [mx].

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>