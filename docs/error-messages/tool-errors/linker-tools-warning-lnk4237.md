---
title: "Upozornění linkerů Lnk4237 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4237
dev_langs: C++
helpviewer_keywords: LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8cc822d4e7432a0a603df9da78b7c4d244719a09
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4237"></a>Upozornění linkerů LNK4237
/SUBSYSTEM:NATIVE zadat při importu z 'dll'; Použijte /SUBSYSTEM:CONSOLE nebo /SUBSYSTEM:WINDOWS.  
  
 [/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) byl zadán při vytváření aplikace systému windows (Win32), který přímo používá jeden nebo více následujících akcí:  
  
-   Kernel32.dll  
  
-   Gdi32.dll  
  
-   User32.dll  
  
-   jeden z knihovny DLL msvcrt *.  
  
 Toto upozornění můžete vyřešit bez zadání **/SUBSYSTEM:NATIVE**.