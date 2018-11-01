---
title: Upozornění linkerů LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 62ce0a0edc7f15bc5a19e4630133976f413da35a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588614"
---
# <a name="linker-tools-warning-lnk4237"></a>Upozornění linkerů LNK4237

Souboru zadat při importu z 'dll'; Použijte/Subsystem: Console nebo/Subsystem: Windows.

[Souboru](../../build/reference/subsystem-specify-subsystem.md) byl zadán při sestavování aplikace systému windows (Win32), který přímo používá jeden nebo více z následujících akcí:

- Kernel32.dll

- Gdi32.dll

- User32.dll

- jeden z msvcrt\* knihovny DLL.

Vyřešit tato upozornění tak, že bez zadání **souboru**.