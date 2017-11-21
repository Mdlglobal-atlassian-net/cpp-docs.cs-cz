---
title: "Pořadí možností CL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords: cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fdcc4b315f2e223e59e88e2f5876965d106a49c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="order-of-cl-options"></a>Pořadí možností CL
Možnosti může vyskytovat kdekoli na příkazovém řádku CL, s výjimkou/Link možnost, která musí objevit jako poslední. Kompilátor začíná zadaný v možnosti [proměnné prostředí CL](../../build/reference/cl-environment-variables.md) a potom načte příkazového řádku zleva doprava – soubory příkazů v pořadí, zjistí jejich zpracování. Každý možnost se vztahuje na všechny soubory na příkazovém řádku. Pokud CL zaznamená konfliktní možnosti, používá jako úplně vpravo.  
  
## <a name="see-also"></a>Viz také  
 [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)