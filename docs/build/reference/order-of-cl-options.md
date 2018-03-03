---
title: "Pořadí možností CL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef67792b01d4d4dab535bfb180cd70beb2316b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="order-of-cl-options"></a>Pořadí možností CL
Možnosti může vyskytovat kdekoli na příkazovém řádku CL, s výjimkou/Link možnost, která musí objevit jako poslední. Kompilátor začíná zadaný v možnosti [proměnné prostředí CL](../../build/reference/cl-environment-variables.md) a potom načte příkazového řádku zleva doprava – soubory příkazů v pořadí, zjistí jejich zpracování. Každý možnost se vztahuje na všechny soubory na příkazovém řádku. Pokud CL zaznamená konfliktní možnosti, používá jako úplně vpravo.  
  
## <a name="see-also"></a>Viz také  
 [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)