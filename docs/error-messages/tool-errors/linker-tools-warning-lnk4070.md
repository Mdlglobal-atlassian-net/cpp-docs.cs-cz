---
title: Upozornění linkerů LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410262"
---
# <a name="linker-tools-warning-lnk4070"></a>Upozornění linkerů LNK4070

/ Out: název_souboru – direktiva v. EXP se liší od názvu výstupního souboru 'filename'; Direktiva se ignoruje

`filename` Zadané v poli [název](../../build/reference/name-c-cpp.md) nebo [KNIHOVNY](../../build/reference/library.md) při vytvoření souboru .exp se liší od výstupu `filename` , která byla ve výchozím nastavení předpokládá nebo zadaný [/OUT](../../build/reference/out-output-file-name.md) možnost.

Toto upozornění se zobrazí, pokud změníte název výstupního souboru ve vývojovém prostředí a ve kterém nebyla aktualizována v souboru .def projektu. Ručně aktualizujte soubor .def vyřešit tato upozornění.

Klientský program, který používá výslednou knihovnu DLL může dojít k potížím.