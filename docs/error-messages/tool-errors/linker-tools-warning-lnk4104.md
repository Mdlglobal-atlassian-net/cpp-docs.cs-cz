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
ms.openlocfilehash: 6d049ef8663798236250977e90d12c2971dec443
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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