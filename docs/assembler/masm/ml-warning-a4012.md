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
ms.workload: cplusplus
ms.openlocfilehash: 0648d2bac0d300fc8e2c696b54741a3d7293a4f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-warning-a4012"></a>Upozornění nástroje ML A4012
**informace o čísle řádku pro segment bez třídy 'kódu.**  
  
 Nebyly pokyny v segment, který neměl název třídy, který končí řetězcem "Kód." Assembleru nevygeneroval CodeView informace o těchto pokynů.  
  
 CodeView nemůže zpracovat moduly s kódem v segmentech s názvy tříd, které na konci "Kód."  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)