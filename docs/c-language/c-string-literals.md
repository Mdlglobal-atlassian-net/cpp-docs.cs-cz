---
title: "Textové literály jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0be3ee70ef708441d20fdbbc14f25f5102d734a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-string-literals"></a>Textové literály jazyka C
"Řetězcový literál" je posloupnost znaků ze zdrojové znakové sady uzavřené v uvozovkách (**""**). Textové literály slouží k reprezentaci posloupnost znaků, které, dohromady, tvoří řetězce ukončené hodnotou null. Je třeba vždy předponu celou textové literály písmenem **L**.  
  
## <a name="syntax"></a>Syntaxe  
 *řetězcový literál*:  
 **"** *s – znak pořadí* opt**"**  
  
 **L"** *s – znak pořadí* opt**"**  
  
 *s – znak pořadí*:  
 *s – znak*  
  
 *s – znak pořadí s – znak*  
  
 *s char*:  
 nastavit kteréhokoli člena znak zdroje, s výjimkou dvojité uvozovky ("), zpětné lomítko (\\), nebo znak nového řádku  
  
 *řídicí sekvence*  
  
 Následující příklad je jednoduchý řetězcový literál:  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 Všechny kódy, které jsou uvedené v vyhnuli [řídicí sekvence](../c-language/escape-sequences.md) tabulky jsou platné v textové literály. Chcete-li představují uvozovky v řetězcový literál, použijte řídicí sekvence  **\\"**. Jednoduché uvozovky (**'**) může být reprezentován bez řídicí sekvence. Zpětné lomítko (**\\**) musí být sledována s druhé zpětné lomítko (**\\\\**) při zobrazí v řetězci. Na konci řádku se zobrazí zpětné lomítko, je vždy interpretovat jako znak pokračování řádku.  
  
## <a name="see-also"></a>Viz také  
 [Elementy jazyka C](../c-language/elements-of-c.md)