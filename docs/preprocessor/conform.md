---
title: v souladu s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs: C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f876c1b921a00c251010d22e2cdd000a405a651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="conform"></a>conform
**Konkrétní C++**  
  
 Určuje chování běhové [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) – možnost kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 Určuje název možnosti kompilátoru má být změněn. Jediné platné *název* je `forScope`.  
  
 **Zobrazit** (volitelné)  
 Způsobí, že aktuální nastavení *název* (true nebo false), který se má zobrazit prostřednictvím upozornění během kompilace. Například `#pragma conform(forScope, show)`.  
  
 **vypnutý**(volitelné)  
 Nastavení *název* k **na** umožňuje [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) – možnost kompilátoru. Výchozí hodnota je **vypnout**.  
  
 **nabízená** (volitelné)  
 Aktuální hodnota nabízených oznámení *název* do zásobníku vnitřní kompilátoru. Pokud zadáte *identifikátor*, můžete zadat **na** nebo **vypnout** hodnota *název* vloženy do zásobníku. Například `#pragma conform(forScope, push, myname, on)`.  
  
 **POP** (volitelné)  
 Nastaví hodnotu *název* na hodnotu v horní části zásobníku vnitřní kompilátoru a bodů POP zásobníku. Pokud je zadán identifikátor s **pop**, zásobníku budou odebrány, zpět, dokud nenajde záznam s *identifikátor*, který bude také být odebrány; aktuální hodnota *název* v na další záznam v zásobníku se změní na novou hodnotu *název*. Pokud zadáte pop s *identifikátor* , není v záznamu v zásobníku, **pop** je ignorována.  
  
 *identifikátor*(volitelné)  
 Může být součástí **nabízené** nebo **pop** příkaz. Pokud *identifikátor* se používá, pak **na** nebo **vypnout** specifikátor lze také použít.  
  
## <a name="example"></a>Příklad  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)