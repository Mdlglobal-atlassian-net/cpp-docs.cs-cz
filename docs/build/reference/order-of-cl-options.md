---
title: Pořadí možností CL (C++) – Visual Studio
ms.date: 12/14/2018
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 93907265bed8141b5c63edd5e75d632e060351fe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811638"
---
# <a name="order-of-cl-options"></a>Pořadí možností CL

Možnosti může vyskytovat kdekoli v příkazovém řádku CL. kromě možností/Link, které se musí objevit jako poslední. Kompilátor začíná možnosti zadané v [proměnné prostředí CL](cl-environment-variables.md) a pak přečte řádek příkazového zleva doprava – zpracování souborů příkazu v pořadí jejich výskytu. Každá možnost se vztahuje na všechny soubory v příkazovém řádku. Pokud CL narazí na kolidující možnosti, používá úplně vpravo možnost.

## <a name="see-also"></a>Viz také:

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
