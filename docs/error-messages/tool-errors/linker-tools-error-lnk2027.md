---
title: Chyba linkerů LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 0c531f70f98a017e8b75cceddc684f99d33bc554
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194590"
---
# <a name="linker-tools-error-lnk2027"></a>Chyba linkerů LNK2027

Nerozpoznaný odkaz na modul – modul

Soubor předaný linkeru má závislost na modulu, který nebyl zadán s **/ASSEMBLYMODULE** ani předán přímo do linkeru.

Chcete-li vyřešit LINKERŮ LNK2027, proveďte jednu z následujících akcí:

- Nepředávejte do linkeru soubor, který má závislost modulu.

- Určete modul pomocí **/ASSEMBLYMODULE**.

- Pokud je modul bezpečný. netmodule, předejte modul přímo linkeru.

Další informace naleznete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) a [souborů. netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md).
