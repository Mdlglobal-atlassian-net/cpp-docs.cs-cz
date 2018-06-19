---
title: Závažná chyba nástroje ML A1017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5fcb2d921a40b35c6022b2aca1e22adc2d8c45e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054680"
---
# <a name="ml-fatal-error-a1017"></a>Závažná chyba nástroje ML A1017
**Chybí název zdrojového souboru**  
  
 ML nelze vyhledat soubor sestavte nebo předat linkeru.  
  
 Tato chyba se vygeneruje, když poskytují možnosti příkazového řádku ML bez zadání filename k provedení akce. Chcete-li uspořádat soubory, které nemají .asm rozšíření, použijte **/Ta** možnost příkazového řádku.  
  
 Tato chyba může být také generována vyvolání ML bez parametrů, pokud ML – proměnná prostředí obsahuje možnosti příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)