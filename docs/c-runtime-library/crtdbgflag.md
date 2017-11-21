---
title: "_crtdbgflag – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs: C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 559dba68c8c171fbc84be17e64c2628b4bbf5011
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crtdbgflag"></a>_crtDbgFlag
**_Crtdbgflag –** příznak se skládá z pěti bitových polí, která řídí jak jsou přidělení paměti na ladicí verze haldy sledovat, ověřit, hlášené a zálohované. Bitová pole vlajky jsou nastavené pomocí [_crtsetdbgflag –](../c-runtime-library/reference/crtsetdbgflag.md) funkce. Tento příznak a jeho bitová pole jsou deklarované v Crtdbg.h. Tento příznak je k dispozici pouze při [_DEBUG –](../c-runtime-library/debug.md) příznak byla definována v aplikaci.  
  
 Další informace o používání tento příznak ve spojení s další funkce ladění najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="see-also"></a>Viz také  
 [Příznaky ovládacích prvků](../c-runtime-library/control-flags.md)