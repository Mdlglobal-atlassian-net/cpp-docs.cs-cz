---
title: "pointers_to_members – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs:
- C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4313aaa38d410b8e6f46594cd9ce11269b523073
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="pointerstomembers"></a>pointers_to_members
**Konkrétní C++**  
  
 Určuje, zda ukazatel na člen třídy lze deklarovat před definicí jeho přidružené třídy, a slouží k řízení velikosti ukazatele a kódu potřebného k interpretaci tohoto ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete umístit **pointers_to_members –** – Direktiva pragma zdrojový soubor jako alternativu k použití [/vmx](../build/reference/vmb-vmg-representation-method.md) – možnosti kompilátoru nebo [klíčová slova dědičnosti](../cpp/inheritance-keywords.md).  
  
 *Ukazatel deklarace* argument určuje, zda mají deklarovány ukazatele na člena, před nebo po definice přidružené funkce. *Ukazatel deklarace* argument je jedním z následujících dvou symboly:  
  
|Argument|Komentáře|  
|--------------|--------------|  
|**full_generality**|Generuje bezpečný, někdy neoptimální kód. Používáte **full_generality** Pokud žádné ukazatele na člena, je deklarovaný před definice přidružené třídy. Tento argument vždy používá reprezentace ukazatel určeného *většinu. Obecná reprezentace* argument. Ekvivalentní možnosti /vmg.|  
|**best_case**|Generuje bezpečný, optimální kód, který používá nejlepší reprezentaci pro všechny odkazy na členy. Vyžaduje definování třídy před deklarací ukazatele na člena této třídy. Výchozí hodnota je **best_case**.|  
  
 *Většinu. Obecná reprezentace* argument určuje nejmenší vyjádření ukazatele, kompilátor bezpečně můžete odkazovat všechny ukazatele na člena třídy v jednotce překlad. Tento argument může nabývat kterékoliv z těchto hodnot:  
  
|Argument|Komentáře|  
|--------------|--------------|  
|**single_inheritance**|Nejobecnější reprezentace je jediná dědičnost, ukazatel na členskou funkci. Způsobí chybu, je-li model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako vícenásobný nebo virtuální.|  
|**multiple_inheritance**|Nejobecnější reprezentace je vícenásobná dědičnost, ukazatel na členskou funkci. Způsobí chybu, je-li model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako virtuální.|  
|**virtual_inheritance**|Nejobecnější reprezentace je virtuální dědičnost, ukazatel na členskou funkci. Nikdy nezpůsobí chybu. Toto je výchozí argument při **#pragma pointers_to_members(full_generality)** se používá.|  
  
> [!CAUTION]
>  Direktivu pragma `pointers_to_members` používejte pouze v souboru zdrojového kódu, který chcete ovlivnit, a až po všech direktivách `#include`. Tímto postupem snížíte riziko, že tato direktiva pragma ovlivní další soubory a že bude náhodně zadáno více definic pro stejnou proměnnou, funkci nebo název třídy.  
  
## <a name="example"></a>Příklad  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## <a name="end-c-specific"></a>Konkrétní END C++  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)