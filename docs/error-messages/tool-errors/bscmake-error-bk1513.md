---
title: Chyba nástroje BSCMAKE BK1513 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93664a1224b85ec808805da0172aec408e875bc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295737"
---
# <a name="bscmake-error-bk1513"></a>Chyba nástroje BSCMAKE BK1513
nonincremental aktualizace vyžaduje všechny. Soubory SBR  
  
 BSCMAKE nemůže vytvořit nový procházení (.bsc) soubor, protože jeden nebo více souborů .sbr se zkrátí. Pro vyhledání názvů souborů zkrácený .sbr, přečtěte si [nástroje BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) upozornění, které náleží k této chybě.  
  
 BSCMAKE můžete aktualizovat souboru BSC souborem zkrácený .sbr ale nemůže vytvořit nový. BSCMAKE může vytvořit nový soubor .bsc z následujících důvodů:  
  
-   Chybějící souboru BSC programem.  
  
-   Nesprávný název souboru zadaný pro souboru BSC programem.  
  
-   Poškozená .bsc soubor.  
  
 Chcete-li tento problém vyřešit, odstraňte soubory .sbr zkrácený a opětovné sestavení, nebo Vyčistit řešení a sestavte znovu. (V prostředí IDE, zvolte **sestavení**, **Vyčistit řešení**a potom zvolte **sestavení**, **znovu sestavit řešení**.)