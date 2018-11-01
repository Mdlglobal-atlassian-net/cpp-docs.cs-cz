---
title: Chyba linkerů LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: e74912780bab3056ead36ae3705f0910805228e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545896"
---
# <a name="linker-tools-error-lnk2027"></a>Chyba linkerů LNK2027

odkaz na nerozpoznaný modulu 'module'

Soubor linkeru předány obsahuje závislost na modulu, který byl zadán ani jeden s **/ASSEMBLYMODULE** ani linkeru předány.

Vyřešit LNK2027, proveďte jednu z následujících akcí:

- Nepředávejte linkeru soubor, který má závislost modulu.

- Zadejte modul s parametrem **/ASSEMBLYMODULE**.

- Pokud modul je bezpečné .netmodule, předejte modulu přímo do propojovacího programu.

Další informace najdete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) a [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).