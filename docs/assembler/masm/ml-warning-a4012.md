---
title: "Upozornění nástroje ML A4012 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A4012
dev_langs: C++
helpviewer_keywords: A4012
ms.assetid: 842b1259-9679-4eeb-a02d-672a583a94e5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b022fcfd49b8be54189e1cfb3b1257338b3409b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-warning-a4012"></a>Upozornění nástroje ML A4012
**informace o čísle řádku pro segment bez třídy 'kódu.**  
  
 Nebyly pokyny v segment, který neměl název třídy, který končí řetězcem "Kód." Assembleru nevygeneroval CodeView informace o těchto pokynů.  
  
 CodeView nemůže zpracovat moduly s kódem v segmentech s názvy tříd, které na konci "Kód."  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)