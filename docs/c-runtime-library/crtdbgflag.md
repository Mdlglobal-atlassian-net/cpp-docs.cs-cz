---
title: _crtdbgflag – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb0c22e65c33ab8f689026e916f550280bf6a8ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgflag"></a>_crtDbgFlag
**_Crtdbgflag –** příznak se skládá z pěti bitových polí, která řídí jak jsou přidělení paměti na ladicí verze haldy sledovat, ověřit, hlášené a zálohované. Bitová pole vlajky jsou nastavené pomocí [_crtsetdbgflag –](../c-runtime-library/reference/crtsetdbgflag.md) funkce. Tento příznak a jeho bitová pole jsou deklarované v Crtdbg.h. Tento příznak je k dispozici pouze při [_DEBUG –](../c-runtime-library/debug.md) příznak byla definována v aplikaci.  
  
 Další informace o používání tento příznak ve spojení s další funkce ladění najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="see-also"></a>Viz také  
 [Příznaky řízení](../c-runtime-library/control-flags.md)