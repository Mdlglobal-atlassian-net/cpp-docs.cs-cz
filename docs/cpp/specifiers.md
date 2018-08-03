---
title: Specifikátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d9898dc6b918643aa8ca4ace34ce2e716344c57
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463486"
---
# <a name="specifiers"></a>Specifikátory
Toto téma popisuje *specifikátory decl* součást (specifikátory deklarace) [deklarace](declarations-and-definitions-cpp.md).  
  
 Následující zástupné symboly a klíčová slova jazyka jsou specifikátory deklarace:  
  
 *specifikátor třídy úložiště*  
  
 *Specifikátor typu*  
  
 *Specifikátor funkce*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef] ( [typedef](http://msdn.microsod) `(` *extended-decl-modifier-seq* `)`  
  
## <a name="remarks"></a>Poznámky  
 *Specifikátory decl* část deklarace je nejdelší sekvence *specifikátory decl* , dá se přenést do název typu bez zahrnutí ukazatel nebo odkaz na modifikátory. Zbývající část deklarace je *deklarátor*, který zahrnuje uvedený název.  
  
 V následující tabulce jsou uvedeny čtyři deklarace a pak zobrazí seznam jednotlivých deklarace *decl-specifers* a *deklarátor* komponenty samostatně.  
  
|Deklarace|*specifikátory decl-*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|**char**|`*lpszAppName`|  
|`typedef char * LPSTR;`|**char**|`*LPSTR`|  
|`const int func1();`|**Const int**|`func1`|  
|`volatile void *pvvObj;`|**volatile void**|`*pvvObj`|  
  
 Protože **podepsané**, **bez znaménka**, **dlouhé**, a **krátký** všechny implikují **int**,  **Definice TypeDef** pojmenujte následující jedním z těchto klíčových slov za člena *seznam deklarátorů* není *specifikátory decl*.  
  
> [!NOTE]
>  Vzhledem k tomu, že lze název předeklarovat, podléhá jeho interpretace poslední deklaraci v aktuálním rozsahu. Redeklarace může ovlivnit, jak jsou názvy interpretovány kompilátorem, zejména **typedef** názvy.  
  
## <a name="see-also"></a>Viz také:  
 [Deklarace a definice](declarations-and-definitions-cpp.md)