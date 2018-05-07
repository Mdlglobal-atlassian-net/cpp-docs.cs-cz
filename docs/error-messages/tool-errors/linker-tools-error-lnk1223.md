---
title: Chyba linkerů Lnk1223 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e50d29af6ac563fadd3a52e5b1d3d15201289083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1223"></a>Chyba linkerů LNK1223
Neplatný nebo poškozený soubor: soubor obsahuje neplatný .pdata příspěvky  
  
 Pro RISC platformy, které používají pdata tato chyba nastane, pokud kompilátor vygenerované .pdata oddíl s neseřazené položky.  
  
 Chcete-li tento problém vyřešit, zkuste kompilování bez [/GL (optimalizace celého programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) povolena. Prázdný funkce těla může také způsobit tuto chybu v některých případech.