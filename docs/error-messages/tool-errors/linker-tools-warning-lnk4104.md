---
title: Upozornění linkerů Lnk4104 | Microsoft Docs
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
ms.openlocfilehash: d9ea3e074cc0db9591cd0ffe9329ff7f1936563f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300950"
---
# <a name="linker-tools-warning-lnk4104"></a>Upozornění linkerů LNK4104
Export symbolu 'symbol' by měl být PRIVÁTNÍ  
  
 `symbol` Může být jedna z následujících akcí:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllGetDocumentation`  
  
-   `DllInitialize`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllRegisterServerExW`  
  
-   `DllUnload`  
  
-   `DllUnregisterServer`  
  
-   `RasCustomDeleteEntryNotify`  
  
-   `RasCustomDial`  
  
-   `RasCustomDialDlg`  
  
-   `RasCustomEntryDlg`  
  
 Toto upozornění je vygenerované při vytváření knihovnu importu pro knihovny DLL a exportování jedné z výše uvedených funkcí bez zadání jako SOUKROMÝ v souboru definice modulu. Obecně platí tyto funkce jsou exportovány pro použití pouze technologie OLE. Umístění do knihovny importu může vést k neobvyklé chování, když program propojené s knihovnou nesprávně provádí volání k nim. Další informace o PRIVATE – klíčové slovo najdete v tématu [EXPORTUJE](../../build/reference/exports.md).