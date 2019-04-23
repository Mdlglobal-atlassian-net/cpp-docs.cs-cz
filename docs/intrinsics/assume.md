---
title: __assume
ms.date: 10/09/2018
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: 1d84e9306dcd468153f38cc0c3085b43388e1dbd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029418"
---
# <a name="assume"></a>__assume

**Microsoft Specific**

Optimalizátor předá pomocného parametru.

## <a name="syntax"></a>Syntaxe

```
__assume(
   expression
)
```

#### <a name="parameters"></a>Parametry

*Výraz*<br/>
Libovolný výraz, který předpokládá, že je vyhodnocen na hodnotu true.

## <a name="remarks"></a>Poznámky

Optimalizátor předpokládá, že podmínka reprezentována `expression` má hodnotu true v místě, kde klíčové slovo se zobrazí a bude platit až do pořád `expression` (například voláním přiřazení k proměnné). Předaný selektivní použití pomocných parametrů optimalizace podle `__assume` může zlepšit optimalizace.

Pokud `__assume` příkazu je zapsán jako rozporu (výraz, který se vždycky vyhodnotí jako false), je vždy považován za `__assume(0)`. Pokud váš kód se nechová podle očekávání, ujistěte se, `expression` jste definovali je platný a hodnotu true, jak je popsáno výše. Další informace o očekávané `__assume(0)` chování, viz dále poznámky.

> [!WARNING]
>  Program nesmí obsahovat neplatný `__assume` příkazu v cestě dostupný. Pokud kompilátor může dosáhnout neplatný `__assume` prohlášení, program může způsobit nepředvídatelné a potenciálně nebezpečné chování.

`__assume` není podstatný vnitřní. Nemusí být deklarovaný jako funkce a nelze ji použít v `#pragma intrinsic` směrnice. I když není vygenerovaný žádný kód, kód vygenerovaný Optimalizátor má vliv.

Použití `__assume` v [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) pouze když kontrolní výraz se nedá vrátit zpátky. Nepoužívejte `__assume` v assert, pro který máte kód pro obnovení další chybě protože kompilátor může optimalizují kód pro zpracování chyb.

`__assume(0)` Příkaz je zvláštní případ. Použití `__assume(0)` označuje cestu kódu, který není dostupný. Následující příklad ukazuje, jak používat `__assume(0)` k označení, že výchozí případ přepínače příkazu není dostupný. Zobrazí se obvykle použití `__assume(0)`.

Z důvodu kompatibility s předchozími verzemi **_assume** je synonymum pro **__assume** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__assume`|x86, ARM, x64|

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

Použití `__assume(0)` Optimalizátor říká, že výchozí případ je nedostupné. Tento příklad ukazuje, že programátor ví, že jediné možné vstupů pro `p` bude 1 nebo 2. Pokud jiná hodnota předána pro `p`, program se stává neplatným a způsobí neočekávané chování.

Kvůli `__assume(0)` příkazu, kompilátor negeneruje kód pro testování, zda `p` má hodnotu, která není zastoupen v příkazu case. Aby to fungovalo `__assume(0)` příkaz musí být prvním příkazem v těle výchozí případ.

Vzhledem k tomu, že kompilátor generuje kód na základě `__assume`, tento kód nemusí pracovat správně, pokud má výraz uvnitř `__assume` příkaz v době běhu je false. Pokud si nejste jisti, že výraz bude vždy hodnotu true v době běhu, můžete použít `assert` funkce k ochraně kód.

```
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Bohužel toto použití `assert` kompilátor zabraňuje provedení výchozí případ optimalizace, která byla popsána dříve v tomto dokumentu. Jako alternativu můžete použít samostatné – makro, následujícím způsobem.

```
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)