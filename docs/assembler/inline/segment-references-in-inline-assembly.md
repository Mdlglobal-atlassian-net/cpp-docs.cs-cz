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
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169250"
---
# <a name="segment-references-in-inline-assembly"></a>Odkazy na segmenty ve vloženém sestavení

**Specifické pro společnost Microsoft**

Je nutné, aby se segmenty odkazovaly podle registru, nikoli podle názvu (název segmentu `_TEXT` není platný, například). Přepsání segmentu musí použít registr explicitně, jako v ES: [BX].

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
