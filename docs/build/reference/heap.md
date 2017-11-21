---
title: -HALDY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /heap
dev_langs: C++
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 709b9a1b57750db4ea8eb13bdaa3d49eed9b7629
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="heap"></a>/HEAP
Nastaví velikost haldy v bajtech. Tato možnost se vztahuje pouze na spustitelné soubory.  
  
```  
  
/HEAP:  
reserve[,commit]  
```  
  
## <a name="remarks"></a>Poznámky  
 `reserve` Argument určuje přidělení celkový počáteční haldy ve virtuální paměti. Ve výchozím nastavení je velikost haldy 1 MB. [Editbin – odkaz](../../build/reference/editbin-reference.md) zaokrouhlí na nejbližší násobek 4 bajtů zadanou hodnotu.  
  
 Volitelné `commit` argument podléhá interpretace v operačním systému. V operačním systému Windows určuje počáteční velikost fyzické paměti k přidělení a množství další paměť přidělit při halda musí být rozbalen. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. A vyšší `commit` hodnota umožňuje systému přidělit paměť, méně často, pokud aplikace vyžaduje více místa na haldy, ale zvyšuje požadavky na paměť a případně doba spuštění aplikace. `commit` Hodnota musí být menší než nebo rovno `reserve` hodnotu.  
  
 Zadejte `reserve` a `commit` hodnoty v desítkový nebo jazyka C šestnáctkové nebo osmičkové soustavě. Například může být zadána hodnota 1 MB jako 1048576 v desítkové soustavě, nebo jako 0x100000 v šestnáctkové soustavě nebo jako 04000000 v osmičková.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)