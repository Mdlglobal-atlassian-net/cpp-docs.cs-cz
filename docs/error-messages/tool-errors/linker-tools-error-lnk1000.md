---
title: Chyba linkerů Lnk1000 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f67df9c53b79fabfc9559380b5b57a72e64cb8a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1000"></a>Chyba linkerů LNK1000
Neznámá chyba; dokumentaci pro možnosti technické podpory  
  
 Poznámka: v případech chyba, zkuste izolovat daný problém a vytvořit reprodukovatelnou testovacího případu, obraťte se na `Microsoft Product Support Services`. Informace o tom, jak prozkoumat a zprávy o těchto chybách naleznete v tématu [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650).  
  
 K této chybě může dojít, pokud zároveň standardní hlavičkových souborů (například dos.h) i vlastní soubory. `#include` hlavičky standardních nejprve následuje vlastní soubory hlaviček.