---
title: "check_stack – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
dev_langs: C++
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6f72036e897a51b907fb41387f25fd7d20df69e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="checkstack"></a>check_stack
Dá pokyn kompilátoru, chcete-li vypnout sondy zásobníku, pokud **vypnout** (nebo  **-** ) není zadaný, nebo zapnout sondy zásobníku, pokud **na** (nebo  **+** ) je zadán.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | -}  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zadána žádný argument, jsou považovány sondy zásobníku podle výchozích nastavení. Tato direktiva pragma se projeví na první funkci definovanou po je vidět – Direktiva pragma. Sondy zásobníku jsou ani součástí, makra ani funkcí, které jsou generované vložené.  
  
 Pokud nemáte poskytnout argument **check_stack –** – Direktiva pragma, kontrola zásobníku se vrátí do nastavení chování na příkazovém řádku. Další informace najdete v tématu [referenční dokumentace kompilátoru](../build/reference/compiler-options.md). Interakci **check_stack – #pragma** a [/Gs](../build/reference/gs-control-stack-checking-calls.md) možnost je shrnuto v následující tabulce.  
  
### <a name="using-the-checkstack-pragma"></a>Pomocí check_stack – direktiva Pragma  
  
|Syntaxe|Kompilovat s<br /><br /> /GS – možnost?|Akce|  
|------------|------------------------------------|------------|  
|**check_stack – #pragma ()** nebo<br /><br /> **check_stack – #pragma**|Ano|Vypnutím kontrola ověření pro funkce, které následují zásobníku|  
|**check_stack – #pragma ()** nebo<br /><br /> **check_stack – #pragma**|Ne|Zapne kontrola ověření pro funkce, které následují zásobníku|  
|**#pragma check_stack(on)**<br /><br /> nebo **check_stack – #pragma +**|Ano nebo ne|Zapne kontrola ověření pro funkce, které následují zásobníku|  
|**#pragma check_stack(off)**<br /><br /> nebo **check_stack – #pragma -**|Ano nebo ne|Vypnutím kontrola ověření pro funkce, které následují zásobníku|  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)