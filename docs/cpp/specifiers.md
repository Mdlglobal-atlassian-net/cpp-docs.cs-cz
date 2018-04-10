---
title: Specifikátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 352ef898c9380c55e90205129ba6fe48bf352856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="specifiers"></a>Specifikátory
Toto téma popisuje *decl specifikátory* součást (specifikátory deklarace) [deklarace](declarations-and-definitions-cpp.md).  
  
 Následující zástupné symboly a klíčová slova jazyka jsou specifikátory deklarace:  
  
 *specifikátor třídy úložiště*  
  
 *specifikace typu*  
  
 *Funkce – specifikátor*  
  
 [Friend](../cpp/friend-cpp.md)  
  
 [Definice TypeDef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [__declspec](../cpp/declspec.md) `(` *rozšířené decl – modifikátor seq*`)`  
  
## <a name="remarks"></a>Poznámky  
 *Decl specifikátory* součástí deklaraci je nejdelší pořadí *decl specifikátory* , můžete provést znamená název typu, není včetně ukazatele, nebo odkaz modifikátory. Zbývající část deklaraci je *deklarátor*, který obsahuje zavedla název.  
  
 Následující tabulka uvádí čtyři deklarace a pak uvádí každý deklarace *decl specifers* a *deklarátor* součást samostatně.  
  
|Deklarace|*specifikátory decl*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 Protože `signed`, `unsigned`, `long`, a `short` všechny implikují `int`, `typedef` název následující jedno z klíčových slov je provést jako člen *deklarátor list* není z *decl specifikátory*.  
  
> [!NOTE]
>  Vzhledem k tomu, že lze název předeklarovat, podléhá jeho interpretace poslední deklaraci v aktuálním rozsahu. Redeklarace může ovlivnit, jak jsou názvy interpretovány kompilátorem, a to zejména názvy `typedef`.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a definice](declarations-and-definitions-cpp.md)