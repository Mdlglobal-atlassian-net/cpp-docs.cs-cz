---
title: Definice a konvence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f227f37f4a9de92f244df5988f7ee8088e41d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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