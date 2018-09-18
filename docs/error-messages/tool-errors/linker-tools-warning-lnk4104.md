---
title: Upozornění Linkerů LNK4104 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6304f3ea928c89f4756a4594270ebb7914324f85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057259"
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