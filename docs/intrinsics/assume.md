---
title: __assume
ms.date: 09/02/2019
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: 06189405703a7cc34f3bd807ec79612394ee899f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368202"
---
# <a name="__assume"></a>__assume

**Specifické pro Microsoft**

Předává nápovědu optimalizátoru.

## <a name="syntax"></a>Syntaxe

```C
__assume(
   expression
)
```

### <a name="parameters"></a>Parametry

*Výraz*\
Libovolný výraz, který se předpokládá, že vyhodnotit true.

## <a name="remarks"></a>Poznámky

Optimalizátor předpokládá, že `expression` podmínka reprezentovaná je true v `expression` místě, kde se zobrazí klíčové slovo a zůstává true, dokud je změněn (například přiřazení k proměnné). Selektivní použití rad předávaných `__assume` optimalizátoru pomocí může zlepšit optimalizaci.

Pokud `__assume` je prohlášení napsáno jako rozpor (výraz, který je vždy vyhodnocen jako false), je vždy považován za `__assume(0)`. Pokud se váš kód nechová podle očekávání, `expression` ujistěte se, že jste definovali je platný a pravdivý, jak je popsáno výše. Další informace o `__assume(0)` očekávaném chování naleznete v pozdějších poznámkách.

> [!WARNING]
> Program nesmí obsahovat `__assume` neplatný příkaz na dosažitelné cestě. Pokud kompilátor může `__assume` dosáhnout neplatný příkaz, program může způsobit nepředvídatelné a potenciálně nebezpečné chování.

`__assume`není skutečnou vnitřní. Nemusí být deklarována jako funkce a nemůže `#pragma intrinsic` být použita ve směrnici. Přestože není generován žádný kód, je ovlivněn kód generovaný optimalizátorem.

Použití `__assume` v [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) pouze v případě, že assert není obnovitelná. Nepoužívejte `__assume` v assert, pro které máte následné chyby pro obnovení kódu, protože kompilátor může optimalizovat pryč kód pro zpracování chyb.

Toto `__assume(0)` prohlášení je zvláštní případ. Slouží `__assume(0)` k označení cesty kódu, která není k zastižení. Následující příklad ukazuje, `__assume(0)` jak použít k označení, že nelze dosáhnout výchozího případu příkazu switch. To ukazuje nejtypičtější `__assume(0)`použití .

Pro kompatibilitu s předchozími verzemi **je _assume** synonymem pro **__assume** pokud není zadána možnost kompilátoru [/Za \(Zakázat rozšíření jazyka).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__assume`|x86, ARM, x64, ARM64|

## <a name="example"></a>Příklad

```cpp
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

Použití `__assume(0)` říká optimalizátoru, že výchozí případ nelze dosáhnout. Příklad ukazuje, že programátor ví, že pouze `p` možné vstupy pro bude 1 nebo 2. Pokud je předána `p`jiná hodnota pro , program se stane neplatným a způsobí nepředvídatelné chování.

V důsledku příkazu `__assume(0)` kompilátor negeneruje kód k `p` testování, zda má hodnotu, která není reprezentována v příkazu case. Aby to fungovalo, `__assume(0)` musí být příkaz prvním příkazem v těle výchozího případu.

Vzhledem k tomu, že `__assume`kompilátor generuje kód založený na `__assume` aplikaci , nemusí tento kód pracovat správně, pokud je výraz uvnitř příkazu za běhu nepravdivý. Pokud si nejste jisti, že výraz bude vždy true `assert` za běhu, můžete použít funkci k ochraně kódu.

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Bohužel toto `assert` použití zabrání kompilátoru z provádění výchozí případ optimalizace, která byla popsána dříve v tomto dokumentu. Jako alternativu můžete použít samostatné makro následujícím způsobem.

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
