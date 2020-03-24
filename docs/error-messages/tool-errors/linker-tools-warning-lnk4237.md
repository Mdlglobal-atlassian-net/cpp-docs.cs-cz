---
title: Upozornění linkerů LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: aaa26393f1ce76d3e1bc40e5ba4978d1bcdb4fc9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193755"
---
# <a name="linker-tools-warning-lnk4237"></a>Upozornění linkerů LNK4237

/SUBSYSTEM: při importu z knihovny DLL byl zadán NATIVNÍ parametr. Použijte/SUBSYSTEM: CONSOLE nebo/SUBSYSTEM: WINDOWS.

[/SUBSYSTEM: nativní](../../build/reference/subsystem-specify-subsystem.md) byl zadán při vytváření aplikace pro Windows (Win32), která přímo používá jednu nebo více z následujících možností:

- kernel32.dll

- gdi32.dll

- user32.dll

- jedna z\* knihoven DLL knihovny Msvcrt.

Vyřešit toto upozornění tím, že neurčíte **/SUBSYSTEM: Native**.
