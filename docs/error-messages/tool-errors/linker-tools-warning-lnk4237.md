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
ms.openlocfilehash: 479bd4ff8a4f48da679c9e17ec100668de84d089
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113705"
---
# <a name="linker-tools-warning-lnk4237"></a>Upozornění linkerů LNK4237

Souboru zadat při importu z 'dll'; Použijte/Subsystem: Console nebo/Subsystem: Windows.

[Souboru](../../build/reference/subsystem-specify-subsystem.md) byl zadán při sestavování aplikace systému windows (Win32), který přímo používá jeden nebo více z následujících akcí:

- Kernel32.dll

- Gdi32.dll

- User32.dll

- jeden z msvcrt\* knihovny DLL.

Vyřešit tato upozornění tak, že bez zadání **souboru**.