---
title: Používání výrazu atexit | Dokumentace Microsoftu
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
ms.openlocfilehash: f4acd81a5420f9fe2685e7570f26fea61691b845
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467401"
---
# <a name="using-atexit"></a>Používání výrazu atexit
S [atexit](../c-runtime-library/reference/atexit.md) funkce, můžete zadat funkci zpracování výstupu, který se spustí před ukončením programu. Žádné globální statické objekty inicializované před voláním **atexit** před spuštěním funkce zpracování výstupu nejsou zničeny.  
  
## <a name="see-also"></a>Viz také:  
 [Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)