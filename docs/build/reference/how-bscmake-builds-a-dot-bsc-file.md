---
title: "Jak BSCMAKE sestavení. Souboru BSC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: adc340a30fcf0292c3dc7fa0e595d488b4046431
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Postupy: Sestavení souboru BSC programem BSCMAKE
BSCMAKE sestavení nebo znovu sestaví souboru BSC nejefektivnějším způsobem, může to. Aby nedocházelo k problémům, je důležité si uvědomit, procesu sestavení.  
  
 Při BSCMAKE sestavení soubor s informacemi o procházení, zkrátí soubory .sbr nule délka. Během následných sestavení stejného souboru soubor .sbr nulové délky (nebo je prázdný) informuje BSCMAKE, zda má soubor .sbr bez nového příspěvku aby. Umožňuje BSCMAKE vědět, že aktualizace té části souboru se nevyžaduje a přírůstkové sestavení jsou dostatečné. Při každé sestavení (Pokud je zadána možnost/n), BSCMAKE se nejprve pokusí přírůstkově aktualizovat soubor pomocí pouze .sbr soubory, které se změnily.  
  
 BSCMAKE hledá .bsc soubor, který má zadaný název s parametrem /o. Pokud není zadán /o, BSCMAKE vyhledá soubor, který má základní název první soubor .sbr a .bsc rozšíření. Pokud soubor existuje, provede BSCMAKE informačního souboru procházet pomocí přispívajících soubory .sbr přírůstkové sestavení. Pokud soubor neexistuje, BSCMAKE provede úplné sestavení pomocí všechny soubory .sbr. Pravidla pro sestavení jsou následující:  
  
-   Pro úplnou sestavení proběhla úspěšně všechny zadané soubory .sbr musí existovat a nesmí se zkrátila. Pokud se zkrátí souboru .sbr, je nutné znovu sestavit ho (pomocí nutnosti rekompilace nebo sestavení) před spuštěním nástroje BSCMAKE.  
  
-   Pro přírůstkové sestavení úspěšné musí existovat souboru BSC programem. Všechny přispívajících soubory .sbr, dokonce i prázdné soubory, musí existovat a musí být zadán v příkazovém řádku BSCMAKE. Pokud vynecháte souboru .sbr z příkazového řádku, BSCMAKE jeho příspěvku odebere ze souboru.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření. Souboru BSC](../../build/reference/building-a-dot-bsc-file.md)