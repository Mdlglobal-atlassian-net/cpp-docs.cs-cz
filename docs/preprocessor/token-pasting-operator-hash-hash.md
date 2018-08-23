---
title: Vložení tokenu (##) – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '##'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dee802a09fd3ade03ac18cac8556d8073b19eb94
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464608"
---
# <a name="token-pasting-operator-"></a>Operátor vložení tokenu (##)
Operátor double znak čísla neboli "vložení tokenu" (**##**), který se někdy nazývá operátor "slučování", se používá v makrech objektu a podobné funkce. Umožňuje sloučit samostatné tokeny do jediného tokenu, a proto nemůže být prvním nebo posledním tokenem v definici makra.  
  
Pokud je formální parametr v definici makra předcházen nebo následován operátorem vložení tokenu, je formální parametr okamžitě nahrazen nerozbaleným vlastním argumentem. Rozšíření makra není na argumentu provedeno před nahrazením.  
  
Poté je každý výskyt operátoru vložení tokenu v *řetězci tokenu* je odebrán a tokeny předcházejí a následují, jsou zřetězeny. Výsledný token musí být platný token. V takovém případě je tento token prověřen pro možná nahrazení, pokud představuje název makra. Identifikátor představuje název, kterým bude tento zřetězený token v programu před nahrazením znám. Každý token představuje token definovaný jinde, buď v programu, nebo na příkazovém řádku kompilátoru. Mezera před nebo za tímto operátorem je nepovinná.  
  
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
  
```cpp  
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