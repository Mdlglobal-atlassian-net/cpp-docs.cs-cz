---
title: Zahrnout soubory pro Multithreading | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62b94f4a7a394b78cb7c6f23275709e4aeacc774
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="include-files-for-multithreading"></a>Zahrnuté soubory pro multithreading
Standardní zahrnout soubory deklarovat funkce běhové knihovny jazyka C, jak jsou implementované v knihovnách. Pokud použijete [úplná optimalizace](../build/reference/ox-full-optimization.md) (/ Ox) nebo [fastcall zásady volání](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) možnost kompilátor předpokládá, že všechny funkce by měla být volána pomocí konvence volání registru. Funkce běhové knihovny byly zkompilovány pomocí konvence volání jazyka C a deklarace v standardní zahrnout soubory oznámení kompilátoru generovat správné externí odkazy na tyto funkce.  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)