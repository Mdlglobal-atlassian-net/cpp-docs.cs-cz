---
title: Kompilování a propojování programů s více vlákny | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c77cb217fe841e15f4c7470340bd3fbb502f6a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="compiling-and-linking-multithread-programs"></a>Kompilování a propojování programů s více vlákny
Bounce.c program byla zavedená v [Ukázkový vícevláknový C Program](../parallel/sample-multithread-c-program.md).  
  
 Kompilované programy s více vlákny ve výchozím nastavení.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Pro zkompilování a spojení s více vlákny programu Bounce.c ve vývojovém prostředí  
  
1.  Na **soubor** nabídky, klikněte na tlačítko **nový**a potom klikněte na **projektu**.  
  
2.  V **typy projektů** podokně klikněte na tlačítko **Win32**.  
  
3.  V **šablony** podokně klikněte na tlačítko **Konzolová aplikace Win32**a zadejte název projektu.  
  
4.  Přidání souboru, který obsahuje zdrojový kód C do projektu.  
  
5.  Na **sestavení** nabídky, sestavení projektu kliknutím **sestavení** příkaz.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Pro zkompilování a spojení s více vlákny program Bounce.c z příkazového řádku  
  
1.  Kompilace a propojení program:  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)