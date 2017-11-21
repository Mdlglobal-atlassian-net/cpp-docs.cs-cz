---
title: Definice a konvence | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fcb72c4e001a087b49967c64b10974ee41cc49ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="definitions-and-conventions"></a>Definice a konvence
Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.  
  
 Terminálově nezávislých jsou zástupné symboly v syntaxi a jsou definovány jinde v této syntaxe souhrnu. Definice mohou být rekurzivní.  
  
 Volitelná součást je označena zkratkou opt. Například  
  
```  
  
{  
expression <SUB>opt</SUB> }  
```  
  
 označuje výraz volitelné uzavřené do složených závorek.  
  
 Konvence syntaxe použít jiné písmo atributy pro různé součásti syntaxe. Symboly a písma jsou následující:  
  
|Atribut|Popis|  
|---------------|-----------------|  
|*nonterminal*|Kurzíva označuje neterminály.|  
|**Const**|Terminály tučného typu jsou slova a symboly vyhrazená literály, které je nutné zadat tak, jak je znázorněno. Znaky v tomto kontextu vždy rozlišují velká a malá písmena.|  
|opt|Neterminály následované opt jsou vždy volitelné.|  
|výchozí písmo|Znaky v sadě popsané nebo uvedené v této řez písma můžete použít jako terminály v příkazech jazyka C.|  
  
 Středník (**:**) nonterminal následující zavádí jeho definice. Alternativní definice jsou uvedeny na samostatné řádky, s výjimkou při uvedena slova "mezi."  
  
## <a name="see-also"></a>Viz také  
 [Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)