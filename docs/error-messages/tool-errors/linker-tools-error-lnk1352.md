---
title: LNK1352 chyba nástrojů linkeru
description: Při pokusu o sloučení nepodporovaného oddílu dojde k chybě LNK1352 nástrojů linkeru.
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908380"
---
# <a name="linker-tools-error-lnk1352"></a>LNK1352 chyba nástrojů linkeru

> '*section_name_1*' a '*section_name_2*' nelze sloučit do různých oddílů

## <a name="remarks"></a>Poznámky

Linker zjistil sloučení oddílu, které není povoleno, protože *section_name_1* a *section_name_2* musí být sloučeny do stejného oddílu. K této chybě například dojde, pokud linker zjistí pokus o sloučení `.stls` oddílu `.tls` a oddílu do různých oddílů.

### <a name="to-correct-this-error"></a>Oprava této chyby

Pro tento problém ověřte možnost [/Merge](../../build/reference/merge-combine-sections.md) na příkazovém řádku linkeru.

## <a name="see-also"></a>Viz také:

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
