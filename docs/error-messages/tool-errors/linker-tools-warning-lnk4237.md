---
title: Upozornění Linkerů LNK4237 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcc109fe3ccf06e0461deed449517850271a2024
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209388"
---
# <a name="linker-tools-warning-lnk4237"></a>Upozornění linkerů LNK4237
Souboru zadat při importu z 'dll'; Použijte/Subsystem: Console nebo/Subsystem: Windows.  
  
 [Souboru](../../build/reference/subsystem-specify-subsystem.md) byl zadán při sestavování aplikace systému windows (Win32), který přímo používá jeden nebo více z následujících akcí:  
  
-   Kernel32.dll  
  
-   Gdi32.dll  
  
-   User32.dll  
  
-   jeden z msvcrt\* knihovny DLL.  
  
 Vyřešit tato upozornění tak, že bez zadání **souboru**.