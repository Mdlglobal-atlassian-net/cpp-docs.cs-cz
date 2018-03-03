---
title: Definice a konvence | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02a6cc8ffcb5748544191673de8f07e87449e806
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|**const**|Terminály tučného typu jsou slova a symboly vyhrazená literály, které je nutné zadat tak, jak je znázorněno. Znaky v tomto kontextu vždy rozlišují velká a malá písmena.|  
|opt|Neterminály následované opt jsou vždy volitelné.|  
|výchozí písmo|Znaky v sadě popsané nebo uvedené v této řez písma můžete použít jako terminály v příkazech jazyka C.|  
  
 Středník (**:**) nonterminal následující zavádí jeho definice. Alternativní definice jsou uvedeny na samostatné řádky, s výjimkou při uvedena slova "mezi."  
  
## <a name="see-also"></a>Viz také  
 [Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)