---
title: Chyba Linkerů LNK1200 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ecd51142bf30230b6b177a36e007345e93bf2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059313"
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200

Chyba při čtení databáze programu: filename.

Nelze načíst databázi programu (PDB).

Tuto chybu může způsobovat poškození souborů.

Pokud `filename` je do souboru PDB soubor objektu znovu zkompilujte soubor objektu pomocí [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Pokud `filename` je soubor PDB pro hlavního výstupního souboru a k této chybě došlo během přírůstkového propojení, odstraňte soubor PDB a znovu připojit.