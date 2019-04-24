---
title: Upozornění linkerů LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298539"
---
# <a name="linker-tools-warning-lnk4104"></a>Upozornění linkerů LNK4104

Export symbolu 'symbol' by měl být PRIVATE.

`symbol` Může být jedna z následujících akcí:

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

Toto upozornění je vygenerován, když jsou sestavování knihovny importů pro knihovnu DLL a exportovat jedné z výše uvedených funkcí bez zadání jako SOUKROMÝ v souboru definice modulu. Obecně tyto funkce jsou exportovány pro použití pouze technologie OLE. Uvedení v knihovně importu může vést k neobvyklé chování při nesprávně propojené ke knihovně program provede volání na ně. Další informace o klíčového slova PRIVATE, naleznete v tématu [EXPORTY](../../build/reference/exports.md).