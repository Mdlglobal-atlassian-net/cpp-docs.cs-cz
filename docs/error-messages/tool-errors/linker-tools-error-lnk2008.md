---
title: Chyba linkerů LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: 97bb2be18da5d166d1d5fba42e4ec8ce1f0439fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386522"
---
# <a name="linker-tools-error-lnk2008"></a>Chyba linkerů LNK2008

Cíl opravy není zarovnaný "symbol_name.

ODKAZ nalezen cíl opravy v souboru objektu, který nebyl správně zarovnány.

Tuto chybu může způsobovat zarovnání vlastní bodu (například #pragma [pack](../../preprocessor/pack.md)), [zarovnat](../../cpp/align-cpp.md) modifikátor, nebo pomocí kódu sestavení jazyka, který upravuje bodu zarovnání.

Pokud váš kód nepoužívá žádné z výše uvedeného, to může být způsobeno kompilátorem.