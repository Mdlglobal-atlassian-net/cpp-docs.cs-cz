---
title: "Upozornění linkerů Lnk4104 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4104
dev_langs: C++
helpviewer_keywords: LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b26286f375f54a20e1d3db534576f692179ade24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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