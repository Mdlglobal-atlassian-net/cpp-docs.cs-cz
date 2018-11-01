---
title: Pořadí možností CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: e5dd07f52f853b17bf663e2fbad7dbe66a3a1db7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633530"
---
# <a name="order-of-cl-options"></a>Pořadí možností CL

Možnosti může vyskytovat kdekoli v příkazovém řádku CL. kromě možností/Link, které se musí objevit jako poslední. Kompilátor začíná možnosti zadané v [proměnné prostředí CL](../../build/reference/cl-environment-variables.md) a pak přečte řádek příkazového zleva doprava – zpracování souborů příkazu v pořadí jejich výskytu. Každá možnost se vztahuje na všechny soubory v příkazovém řádku. Pokud CL narazí na kolidující možnosti, používá úplně vpravo možnost.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)