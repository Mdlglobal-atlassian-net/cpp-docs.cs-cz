---
title: Pořadí možností CL | Microsoft Docs
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
ms.openlocfilehash: 165e20eefecd20ad9dec9e01b38c5eaa7926e4eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="order-of-cl-options"></a>Pořadí možností CL
Možnosti může vyskytovat kdekoli na příkazovém řádku CL, s výjimkou/Link možnost, která musí objevit jako poslední. Kompilátor začíná zadaný v možnosti [proměnné prostředí CL](../../build/reference/cl-environment-variables.md) a potom načte příkazového řádku zleva doprava – soubory příkazů v pořadí, zjistí jejich zpracování. Každý možnost se vztahuje na všechny soubory na příkazovém řádku. Pokud CL zaznamená konfliktní možnosti, používá jako úplně vpravo.  
  
## <a name="see-also"></a>Viz také  
 [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)