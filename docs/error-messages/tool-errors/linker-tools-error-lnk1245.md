---
title: Chyba linkerů LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 4cf9a6c4356872b727a10a360396e51e38928b29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505479"
---
# <a name="linker-tools-error-lnk1245"></a>Chyba linkerů LNK1245

Neplatný subsystém zadaný; subsystému / SUBSYSTEM musí být WINDOWS, WINDOWSCE nebo CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) byla použita pro kompilaci objektu a byl jeden z následujících podmínek hodnotu true:

- Byl definován vlastní vstupní bod ([/Entry](../../build/reference/entry-entry-point-symbol.md)), tak, aby linker nebylo možné odvodit podsystému.

- Byl předán hodnotu [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) – možnost linkeru, který není platný pro objekty/CLR.

V obou situacích je řešení zadejte platnou hodnotu pro možnost linker/Subsystem.