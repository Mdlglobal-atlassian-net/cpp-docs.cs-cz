---
title: Chyba linkerů LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 19e3f820b5bd7fdd8eac2f7b5a96fb5923ae0b92
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183797"
---
# <a name="linker-tools-error-lnk1245"></a>Chyba linkerů LNK1245

byl zadán neplatný podsystém Subsystem; /SUBSYSTEM musí být WINDOWS, WINDOWSCE nebo CONSOLE.

pro zkompilování objektu byly použity hodnoty [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) a jedna z následujících podmínek byla pravdivá:

- Byl definován vlastní vstupní bod ([/entry](../../build/reference/entry-entry-point-symbol.md)), například linker nemůže odvodit podsystém.

- Do Možnosti linkeru [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) , která není platná pro objekty/CLR, byla předána hodnota.

V obou případech je řešením zadat platnou hodnotu pro možnost linkeru/SUBSYSTEM.
