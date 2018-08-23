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
ms.openlocfilehash: 8c1fb739d5e6206297e52fd9103cbba98c5eef01
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42464637"
---
# <a name="specifiers"></a>Specifikátory
Toto téma popisuje *specifikátory decl* součást (specifikátory deklarace) [deklarace](declarations-and-definitions-cpp.md).  
  
 Následující zástupné symboly a klíčová slova jazyka jsou specifikátory deklarace:  
  
 *specifikátor třídy úložiště*  
  
 *Specifikátor typu*  
  
 *Specifikátor funkce*  
  
 [friend](friend-cpp.md)  
 
 [Definice TypeDef](aliases-and-typedefs-cpp.md) `(` *extended-decl-modifier-seq* `)`  

 [__declspec](declspec.md) `(` *extended-decl-modifier-seq* `)`  
  
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
