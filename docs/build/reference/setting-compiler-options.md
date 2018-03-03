---
title: "Nastavení možností kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dbbc7111ceae2353e8bc9820ead319556ce0016b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setting-compiler-options"></a>Nastavení možností kompilátoru
Možnosti kompilátoru jazyka C++ a C lze nastavit buď ve vývojovém prostředí, nebo na příkazovém řádku.  
  
## <a name="in-the-development-environment"></a>Ve vývojovém prostředí  
 Můžete nastavit možnosti kompilátoru pro každý projekt v jeho **stránky vlastností** dialogové okno. V levém podokně vyberte **vlastnosti konfigurace**, **C/C++** a potom vyberte kategorii – možnost kompilátoru. V tématech pro jednotlivé možnosti kompilátoru je popsáno, jak tento parametr nastavíte a kde ho ve vývojovém prostředí najdete. V tématu [– možnosti kompilátoru](../../build/reference/compiler-options.md) úplný seznam.  
  
## <a name="outside-the-development-environment"></a>Mimo vývojové prostředí  
 Možnosti kompilátoru (CL.exe) je možné nastavit:  
  
-   [Na příkazovém řádku](../../build/reference/compiler-command-line-syntax.md)  
  
-   [V příkazové soubory](../../build/reference/cl-command-files.md)  
  
-   [Proměnné prostředí CL](../../build/reference/cl-environment-variables.md)  
  
 Možnosti zadané v proměnné prostředí CL se používají při každém vyvolání CL. Pokud je v proměnné prostředí CL nebo na příkazovém řádku uveden název souboru příkazů, použijí se možnosti zadané v tomto souboru příkazů. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.  
  
 Možnosti kompilátoru se zpracovávají „zleva doprava“ a při zjištění konfliktu platí poslední parametr (nejvíce vpravo). Proměnná prostředí CL se zpracovává před příkazovým řádkem, takže v případě konfliktů mezi proměnnou prostředí CL a příkazovým řádkem má přednost příkazový řádek.  
  
## <a name="additional-compiler-topics"></a>Další témata týkající se kompilátoru  
  
-   [Rychlá kompilace](../../build/reference/fast-compilation.md)  
  
-   [CL vyvolává linker](../../build/reference/cl-invokes-the-linker.md)  
  
## <a name="see-also"></a>Viz také  
 [Odkaz sestavení C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)