---
title: Pořadí možností CL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffe9a440396df14823775db335e52bca6cacdb3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725020"
---
# <a name="order-of-cl-options"></a>Pořadí možností CL

Možnosti může vyskytovat kdekoli v příkazovém řádku CL. kromě možností/Link, které se musí objevit jako poslední. Kompilátor začíná možnosti zadané v [proměnné prostředí CL](../../build/reference/cl-environment-variables.md) a pak přečte řádek příkazového zleva doprava – zpracování souborů příkazu v pořadí jejich výskytu. Každá možnost se vztahuje na všechny soubory v příkazovém řádku. Pokud CL narazí na kolidující možnosti, používá úplně vpravo možnost.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)