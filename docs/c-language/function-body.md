---
title: Funkce text | Microsoft Docs
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
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a0c85ecf0752ff34bf5b61e42309360f2bc4d448
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="function-body"></a>Tělo funkce
"Tělo funkce" je složené příkazu, který obsahuje příkazy, které určují, jaké funkce.  
  
## <a name="syntax"></a>Syntaxe  
 *definice funkce*:  
 *specifikátory deklarace* vyjádřit výslovný*atribut seq* opt*deklarátor deklarace list* opt*složené – příkaz*  
  
 /\**atribut seq* je specifické pro Microsoft * /  
  
 *příkaz složené*: /\* tělo funkce\*/  
 **{***seznam prohlášení* opt*seznam příkazů* opt**}**   
  
 Mít proměnných deklarovaných v těle funkce na "místní proměnné," **automaticky** třídy úložiště, pokud není uvedeno jinak. Při volání funkce úložiště se vytvoří pro místní proměnné a jsou prováděny místní inicializacích. Řízení provádění předá první příkaz v *složené příkaz* a pokračuje v až `return` spustit příkaz nebo je nalezen konec tělo funkce. Ovládací prvek pak vrátí do bodu, kdy byla zavolána funkce.  
  
 A `return` příkazu, který obsahuje výraz, je třeba spustit, pokud je funkce vrátit hodnotu. Pokud žádný není definován návratovou hodnotu funkce `return` spustit příkaz nebo, pokud `return` příkaz neobsahuje výraz.  
  
## <a name="see-also"></a>Viz také  
 [Definice funkcí jazyka C](../c-language/c-function-definitions.md)