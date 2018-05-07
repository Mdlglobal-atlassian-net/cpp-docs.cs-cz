---
title: __assume | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __assume
- __assume_cpp
dev_langs:
- C++
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec83775a007e3a07582f218c5588ae4fe7909b20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="assume"></a>__assume
**Konkrétní Microsoft**  
  
 Předá nápovědu okně Optimalizace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__assume(  
   expression  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 `expression`  
 Všechny výraz, který se předpokládá, že vyhodnotit na hodnotu true.  
  
## <a name="remarks"></a>Poznámky  
 Pro optimalizaci předpokládá, že podmínka reprezentována `expression` platí v místě, kde se zobrazí klíčové slovo a zůstane hodnota true, dokud `expression` je upraveném (například přiřazení proměnné). Selektivní použití pomocných parametrů předaný Optimalizátor podle `__assume` může zlepšit optimalizace.  
  
 Pokud `__assume` příkaz je zapsána jako v rozporu (výraz, který bude vždy vyhodnocena jako false), vždycky je považován za `__assume(0)`. Pokud váš kód není chovají podle očekávání, ověřte, že `expression` jste definovali je platná a nastavena hodnota true, jak je popsáno výše. Další informace o očekává `__assume(0)` chování, najdete v části novější poznámky.  
  
> [!WARNING]
>  Program nesmí obsahovat neplatný `__assume` příkaz dostupný cestou. Pokud kompilátor může dosáhnout neplatný `__assume` příkaz, program může způsobit nepředvídatelné a potenciálně nebezpečná chování.  
  
 `__assume` není podstatný vnitřní. Nemusí být deklarována jako funkce a nelze jej použít v `#pragma intrinsic` – direktiva. I když se generuje žádný kód, kód vygenerovaný Optimalizátor má vliv.  
  
 Použití `__assume` v [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) pouze když assert není použitelná pro obnovení. Nepoužívejte `__assume` v assert, pro které máte kód pro obnovení další chybě protože kompilátor může rychle optimalizovat kód pro ošetření chyb.  
  
 `__assume(0)` Příkaz je zvláštní případ. Použití `__assume(0)` udávajících kód cestu, která je nedostupné. Následující příklad ukazuje, jak používat `__assume(0)` indikující, že v případě výchozí příkaz switch není dostupný. To ukazuje nejčastější použití `__assume(0)`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__assume`|x86 ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## <a name="example"></a>Příklad  
  
```  
// compiler_intrinsics__assume.cpp  
#ifdef DEBUG  
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )  
#else  
# define ASSERT(e)    ( __assume(e) )  
#endif  
  
void func1(int i)  
{  
}  
  
int main(int p)  
{  
   switch(p){  
      case 1:  
         func1(1);  
         break;  
      case 2:  
         func1(-1);  
         break;  
      default:  
         __assume(0);  
            // This tells the optimizer that the default  
            // cannot be reached. As so, it does not have to generate  
            // the extra code to check that 'p' has a value   
            // not represented by a case arm. This makes the switch   
            // run faster.  
   }  
}  
```  
  
 Použití `__assume(0)` informuje okně Optimalizace, není dosažitelná případ výchozí. Příklad ukazuje, že programátorů ví, že možný jenom vstup pro `p` bude 1 nebo 2. Pokud je předaná jinou hodnotu `p`, program se stává neplatným a způsobí, že nepředvídatelné chování.  
  
 Na základě těchto `__assume(0)` příkaz, kompilátor nevygeneruje žádný kód k testování zda `p` má hodnotu, která není v příkazu case reprezentována. Tento postup vyžaduje `__assume(0)` příkaz musí být první příkaz v těle výchozí případu.  
  
 Protože kompilátor generuje kód na základě `__assume`, tento kód nefunguje správně, pokud výraz uvnitř `__assume` příkaz je false v době běhu. Pokud si nejste jisti, že výraz bude vždy hodnotu true v době běhu, můžete použít `assert` funkce k ochraně kód.  
  
```  
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )  
```  
  
 Bohužel, toto využití `assert` zabrání kompilátoru provádění optimalizace výchozí případ, která byla popsána dříve v tomto dokumentu. Jako alternativu můžete použít samostatné makro, následujícím způsobem.  
  
```  
#ifdef DEBUG  
# define NODEFAULT   ASSERT(0)  
#else  
# define NODEFAULT   __assume(0)  
#endif  
  
   default:  
      NODEFAULT;  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)