---
title: Upozornění linkerů LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: 75ca9ec92bbba1c15efc11a731b3894ea03e33dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651422"
---
# <a name="linker-tools-warning-lnk4001"></a>Upozornění linkerů LNK4001

jste; žádné soubory objektů použily se knihovny.

Jeden nebo více souborů .lib, ale ne soubory .obj byl předán linkeru.

Protože propojovací program není schopen získat přístup k informacím v .lib soubor, který je schopen získat přístup v souboru .obj, toto upozornění signalizuje, že je nutné explicitně zadat další možnosti linkeru. Například budete muset zadat [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), nebo [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti.