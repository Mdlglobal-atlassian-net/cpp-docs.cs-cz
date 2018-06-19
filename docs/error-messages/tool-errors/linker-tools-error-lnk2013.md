---
title: Chyba linkerů Lnk2013 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9320b9ead0276b6fb5e1b9773260049a01520e12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299848"
---
# <a name="linker-tools-error-lnk2013"></a>Chyba linkerů LNK2013
opravte typ opravou přetečení. Cílový 'název symbolu' je mimo rozsah  
  
 Linker nemůže pojmout potřebné adresy nebo posun do uvedené instrukce, protože cílový symbol je příliš vzdálený od umístění instrukce.  
  
 Tento problém můžete vyřešit tak, že vytvoříte více bitových kopií nebo pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) možnost tak instrukce a cíle jsou společně blíž oblasti.  
  
 Pokud je název symbolu symbol definovaný uživatelem (nikoli symbol vygenerovaný kompilátorem), lze pro odstranění chyby zkusit také následující akce:  
  
-   Změnit statickou funkci na nestatickou.  
  
-   Přejmenovat část kódu obsahující statickou funkci, aby byla stejná jako volající.  
  
 Chcete-li zjistit, zda je funkce statická, použijte příkaz `DUMPBIN /SYMBOLS`.