---
title: "Chyba linkerů Lnk2013 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2013
dev_langs: C++
helpviewer_keywords: LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37d6fac7ff5f9fae061ed44c639d3d3de1e9fbda
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2013"></a>Chyba linkerů LNK2013
opravte typ opravou přetečení. Cílový 'název symbolu' je mimo rozsah  
  
 Linker nemůže pojmout potřebné adresy nebo posun do uvedené instrukce, protože cílový symbol je příliš vzdálený od umístění instrukce.  
  
 Tento problém můžete vyřešit tak, že vytvoříte více bitových kopií nebo pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) možnost tak instrukce a cíle jsou společně blíž oblasti.  
  
 Pokud je název symbolu symbol definovaný uživatelem (nikoli symbol vygenerovaný kompilátorem), lze pro odstranění chyby zkusit také následující akce:  
  
-   Změnit statickou funkci na nestatickou.  
  
-   Přejmenovat část kódu obsahující statickou funkci, aby byla stejná jako volající.  
  
 Chcete-li zjistit, zda je funkce statická, použijte příkaz `DUMPBIN /SYMBOLS`.