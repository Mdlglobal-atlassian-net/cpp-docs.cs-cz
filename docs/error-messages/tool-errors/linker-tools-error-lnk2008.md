---
title: Chyba Linkerů LNK2008 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eda06e7f133ada4de1b7ec28ac21be205a71f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086808"
---
# <a name="linker-tools-error-lnk2008"></a>Chyba linkerů LNK2008

Cíl opravy není zarovnaný "symbol_name.

ODKAZ nalezen cíl opravy v souboru objektu, který nebyl správně zarovnány.

Tuto chybu může způsobovat zarovnání vlastní bodu (například #pragma [pack](../../preprocessor/pack.md)), [zarovnat](../../cpp/align-cpp.md) modifikátor, nebo pomocí kódu sestavení jazyka, který upravuje bodu zarovnání.

Pokud váš kód nepoužívá žádné z výše uvedeného, to může být způsobeno kompilátorem.