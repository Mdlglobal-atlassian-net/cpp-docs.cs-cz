---
title: Používání výrazu atexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb0c89c34b5107326a961e874289d20cbd2385c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420964"
---
# <a name="using-atexit"></a>Používání výrazu atexit
Pomocí [atexit](../c-runtime-library/reference/atexit.md) funkce, můžete zadat ukončení zpracování funkce, která spustí před ukončení programu. Před spuštěním funkce zpracování výstupu nejsou zničeny žádné globální statické objekty inicializované před voláním funkce `atexit`.  
  
## <a name="see-also"></a>Viz také  
 [Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)