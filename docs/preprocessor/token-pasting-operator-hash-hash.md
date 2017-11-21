---
title: "Vložení tokenu operátoru (#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '##'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5573107688968026bf98eda4b18223e35b7b3ef2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="token-pasting-operator-"></a>Operátor vložení tokenu (##)
Operátor double. číslo podepsání nebo "vložení tokenu" (**##**), která se někdy označuje jako "slučovat" operátor je používán jako objekt a funkce jako makra. Umožňuje sloučit samostatné tokeny do jediného tokenu, a proto nemůže být prvním nebo posledním tokenem v definici makra.  
  
 Pokud je formální parametr v definici makra předcházen nebo následován operátorem vložení tokenu, je formální parametr okamžitě nahrazen nerozbaleným vlastním argumentem. Rozšíření makra není na argumentu provedeno před nahrazením.  
  
 Potom všechny výskyty operátor vložení tokenu v *token řetězec* je odebrán, a jsou zřetězeny tokeny předcházející a následující ho. Výsledný token musí být platný token. V takovém případě je tento token prověřen pro možná nahrazení, pokud představuje název makra. Identifikátor představuje název, kterým bude tento zřetězený token v programu před nahrazením znám. Každý token představuje token definovaný jinde, buď v programu, nebo na příkazovém řádku kompilátoru. Mezera před nebo za tímto operátorem je nepovinná.  
  
 Tento příklad ukazuje použití operátorů převodu na řetězec a vložení tokenu v určeném výstupu programu:  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
 Je-li makro voláno s číselným argumentem jako  
  
```  
paster( 9 );  
```  
  
 vrátí makro výraz  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
 , který se stane  
  
```  
printf_s( "token9 = %d", token9 );  
```  
  
## <a name="example"></a>Příklad  
  
```  
// preprocessor_token_pasting.cpp  
#include <stdio.h>  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
  
int main()  
{  
   paster(9);  
}  
```  
  
```Output  
token9 = 9  
```  
  
## <a name="see-also"></a>Viz také  
 [Operátory preprocesoru](../preprocessor/preprocessor-operators.md)