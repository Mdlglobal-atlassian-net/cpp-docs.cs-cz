---
title: "Chyba linkerů Lnk1223 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1223
dev_langs: C++
helpviewer_keywords: LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41d3de1080fd6b1cc3e8fbc5ca948482229f306e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1223"></a>Chyba linkerů LNK1223
Neplatný nebo poškozený soubor: soubor obsahuje neplatný .pdata příspěvky  
  
 Pro RISC platformy, které používají pdata tato chyba nastane, pokud kompilátor vygenerované .pdata oddíl s neseřazené položky.  
  
 Chcete-li tento problém vyřešit, zkuste kompilování bez [/GL (optimalizace celého programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) povolena. Prázdný funkce těla může také způsobit tuto chybu v některých případech.