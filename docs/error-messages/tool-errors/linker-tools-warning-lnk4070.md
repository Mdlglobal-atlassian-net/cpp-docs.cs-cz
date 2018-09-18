---
title: Upozornění Linkerů LNK4070 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb4ae1c5440742c491d9615a2b4929a9b04f66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106939"
---
# <a name="linker-tools-warning-lnk4070"></a>Upozornění linkerů LNK4070

/ Out: název_souboru – direktiva v. EXP se liší od názvu výstupního souboru 'filename'; Direktiva se ignoruje

`filename` Zadané v poli [název](../../build/reference/name-c-cpp.md) nebo [KNIHOVNY](../../build/reference/library.md) při vytvoření souboru .exp se liší od výstupu `filename` , která byla ve výchozím nastavení předpokládá nebo zadaný [/OUT](../../build/reference/out-output-file-name.md) možnost.

Toto upozornění se zobrazí, pokud změníte název výstupního souboru ve vývojovém prostředí a ve kterém nebyla aktualizována v souboru .def projektu. Ručně aktualizujte soubor .def vyřešit tato upozornění.

Klientský program, který používá výslednou knihovnu DLL může dojít k potížím.