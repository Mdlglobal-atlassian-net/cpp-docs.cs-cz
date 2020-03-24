---
title: Upozornění linkerů LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193963"
---
# <a name="linker-tools-warning-lnk4104"></a>Upozornění linkerů LNK4104

Export symbolu symbol by měl být privátní.

`symbol` může být jedna z následujících:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

Toto upozornění je generováno při sestavování knihovny importu pro knihovnu DLL a exportu jedné z výše uvedených funkcí, aniž by bylo nutné je zadat v souboru definice modulu jako privátní. Obecně platí, že tyto funkce jsou exportovány pro použití pouze pomocí technologie OLE. Jejich umístění do knihovny importů může vést k neobvyklému chování, když program propojený do knihovny nesprávně provede volání do těchto knihoven. Další informace o klíčovém slově PRIVATE naleznete v tématu [EXPORTS](../../build/reference/exports.md).
