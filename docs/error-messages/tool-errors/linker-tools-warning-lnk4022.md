---
title: "Upozornění linkerů Lnk4022 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4022
dev_langs: C++
helpviewer_keywords: LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e35974a72de349f94f2189f676b6dc955c48fab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4022"></a>Upozornění linkerů LNK4022
Nelze najít jedinečný shodu pro symbol "symbol.  
  
 ODKAZ nebo LIB nalezeno více odpovídá pro daný symbol bez upraveného a nebylo možné přeložit nejednoznačnosti. Vytváří žádná výstupní soubor (.exe, .dll, .exp nebo .lib). Toto upozornění je následován jeden upozornění [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pro každou duplicitní symbol a nakonec následuje závažná chyba [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Aby se toto upozornění, zadejte symbol v jeho dekorované formuláře. Spustit [DUMPBIN](../../build/reference/dumpbin-options.md) na objekt můžete zobrazit dekorované názvy.