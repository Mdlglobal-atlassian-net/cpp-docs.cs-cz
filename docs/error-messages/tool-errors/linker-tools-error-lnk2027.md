---
title: Chyba Linkerů LNK2027 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 022e363af575e29e3085dcaec21257fa7e4ab5f1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116840"
---
# <a name="linker-tools-error-lnk2027"></a>Chyba linkerů LNK2027

odkaz na nerozpoznaný modulu 'module'

Soubor linkeru předány obsahuje závislost na modulu, který byl zadán ani jeden s **/ASSEMBLYMODULE** ani linkeru předány.

Vyřešit LNK2027, proveďte jednu z následujících akcí:

- Nepředávejte linkeru soubor, který má závislost modulu.

- Zadejte modul s parametrem **/ASSEMBLYMODULE**.

- Pokud modul je bezpečné .netmodule, předejte modulu přímo do propojovacího programu.

Další informace najdete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) a [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).