---
title: Chyba linkerů LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 00041e677ac7b69df9981551ee3b6cc18f9eb33d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183758"
---
# <a name="linker-tools-error-lnk1264"></a>Chyba linkerů LNK1264

/LTCG: PGINSTRUMENT není k dispozici, ale není vyžadováno generování kódu; instrumentace se nezdařila

**/LTCG: PGINSTRUMENT** byl zadán, ale nebyly nalezeny žádné soubory. obj, které byly zkompilovány s [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentace nemůže probíhat a odkaz se nezdařil. Musí existovat alespoň jeden soubor. obj na příkazovém řádku, který je zkompilován s **/GL** , aby mohlo dojít k instrumentaci.

Optimalizace na základě profilu (PGO) je k dispozici pouze v 64 kompilátorech.
