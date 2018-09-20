---
title: Kompilování a propojování programů s více vlákny | Dokumentace Microsoftu
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
ms.openlocfilehash: 7d9dcb1d7cbda7eebcede4d25de276948d638034
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412922"
---
# <a name="compiling-and-linking-multithread-programs"></a>Kompilování a propojování programů s více vlákny

Bounce.c program je zavedený [Ukázkový vícevláknový Program v jazyce C](sample-multithread-c-program.md).

Jsou zkompilovány programů s více vlákny ve výchozím nastavení.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Chcete-li zkompilovat a propojit s více vlákny program Bounce.c z vývojového prostředí

1. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.

1. V **typy projektů** podokně klikněte na tlačítko **Win32**.

1. V **šablony** podokně klikněte na tlačítko **Konzolová aplikace Win32**a potom zadejte název projektu.

1. Přidáte soubor obsahující zdrojový kód jazyka C do projektu.

1. Na **sestavení** nabídky, sestavte projekt kliknutím **sestavení** příkazu.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Chcete-li zkompilovat a propojit s více vlákny program Bounce.c z příkazového řádku

1. Zkompilujte a propojte program:

    ```
    CL BOUNCE.C
    ```

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)