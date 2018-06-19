---
title: Upozornění linkerů Lnk4022 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cffb9c4c67bc3003b8dcdda0ad3a2e8d55abe932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300368"
---
# <a name="linker-tools-warning-lnk4022"></a>Upozornění linkerů LNK4022
Nelze najít jedinečný shodu pro symbol "symbol.  
  
 ODKAZ nebo LIB nalezeno více odpovídá pro daný symbol bez upraveného a nebylo možné přeložit nejednoznačnosti. Vytváří žádná výstupní soubor (.exe, .dll, .exp nebo .lib). Toto upozornění je následován jeden upozornění [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pro každou duplicitní symbol a nakonec následuje závažná chyba [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Aby se toto upozornění, zadejte symbol v jeho dekorované formuláře. Spustit [DUMPBIN](../../build/reference/dumpbin-options.md) na objekt můžete zobrazit dekorované názvy.