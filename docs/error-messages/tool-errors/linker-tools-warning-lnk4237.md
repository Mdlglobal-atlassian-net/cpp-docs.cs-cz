---
title: Upozornění linkerů Lnk4237 | Microsoft Docs
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
ms.openlocfilehash: 5acccf52d3738985c7a83432342952af03bf78b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4237"></a>Upozornění linkerů LNK4237
/SUBSYSTEM:NATIVE zadat při importu z 'dll'; Použijte /SUBSYSTEM:CONSOLE nebo /SUBSYSTEM:WINDOWS.  
  
 [/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) byl zadán při vytváření aplikace systému windows (Win32), který přímo používá jeden nebo více následujících akcí:  
  
-   Kernel32.dll  
  
-   Gdi32.dll  
  
-   User32.dll  
  
-   jeden z knihovny DLL msvcrt *.  
  
 Toto upozornění můžete vyřešit bez zadání **/SUBSYSTEM:NATIVE**.