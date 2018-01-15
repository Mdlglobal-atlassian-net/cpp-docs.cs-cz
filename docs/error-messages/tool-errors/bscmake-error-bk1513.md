---
title: "Chyba nástroje BSCMAKE BK1513 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1513
dev_langs: C++
helpviewer_keywords: BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ec1e317dcd686a76efba8b8ea8e4782246a3a87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1513"></a>Chyba nástroje BSCMAKE BK1513
nonincremental aktualizace vyžaduje všechny. Soubory SBR  
  
 BSCMAKE nemůže vytvořit nový procházení (.bsc) soubor, protože jeden nebo více souborů .sbr se zkrátí. Pro vyhledání názvů souborů zkrácený .sbr, přečtěte si [nástroje BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) upozornění, které náleží k této chybě.  
  
 BSCMAKE můžete aktualizovat souboru BSC souborem zkrácený .sbr ale nemůže vytvořit nový. BSCMAKE může vytvořit nový soubor .bsc z následujících důvodů:  
  
-   Chybějící souboru BSC programem.  
  
-   Nesprávný název souboru zadaný pro souboru BSC programem.  
  
-   Poškozená .bsc soubor.  
  
 Chcete-li tento problém vyřešit, odstraňte soubory .sbr zkrácený a opětovné sestavení, nebo Vyčistit řešení a sestavte znovu. (V prostředí IDE, zvolte **sestavení**, **Vyčistit řešení**a potom zvolte **sestavení**, **znovu sestavit řešení**.)