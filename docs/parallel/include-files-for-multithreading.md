---
title: Zahrnout soubory pro Multithreading | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f71b52bca5f636d80f2d55cc5e9ffc3e217d90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="include-files-for-multithreading"></a>Zahrnuté soubory pro multithreading
Standardní zahrnout soubory deklarovat funkce běhové knihovny jazyka C, jak jsou implementované v knihovnách. Pokud použijete [úplná optimalizace](../build/reference/ox-full-optimization.md) (/ Ox) nebo [fastcall zásady volání](../build/reference/gd-gr-gv-gz-calling-convention.md) (/ Gr) možnost kompilátor předpokládá, že všechny funkce by měla být volána pomocí konvence volání registru. Funkce běhové knihovny byly zkompilovány pomocí konvence volání jazyka C a deklarace v standardní zahrnout soubory oznámení kompilátoru generovat správné externí odkazy na tyto funkce.  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)