---
title: Upozornění Linkerů LNK4001 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f684e85233c4df777a53f03f07936137c425946e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070416"
---
# <a name="linker-tools-warning-lnk4001"></a>Upozornění linkerů LNK4001

jste; žádné soubory objektů použily se knihovny.

Jeden nebo více souborů .lib, ale ne soubory .obj byl předán linkeru.

Protože propojovací program není schopen získat přístup k informacím v .lib soubor, který je schopen získat přístup v souboru .obj, toto upozornění signalizuje, že je nutné explicitně zadat další možnosti linkeru. Například budete muset zadat [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), nebo [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti.