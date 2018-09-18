---
title: Chyba Linkerů LNK1245 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef7bace5cec937399d7a2ed440e21b9b751f4141
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041789"
---
# <a name="linker-tools-error-lnk1245"></a>Chyba linkerů LNK1245

Neplatný subsystém zadaný; subsystému / SUBSYSTEM musí být WINDOWS, WINDOWSCE nebo CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) byla použita pro kompilaci objektu a byl jeden z následujících podmínek hodnotu true:

- Byl definován vlastní vstupní bod ([/Entry](../../build/reference/entry-entry-point-symbol.md)), tak, aby linker nebylo možné odvodit podsystému.

- Byl předán hodnotu [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) – možnost linkeru, který není platný pro objekty/CLR.

V obou situacích je řešení zadejte platnou hodnotu pro možnost linker/Subsystem.