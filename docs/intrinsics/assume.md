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
ms.openlocfilehash: f3f847b5268605bdc5df90a8bbc6a88c78431864
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216960"
---
# <a name="__assume"></a>__assume

**Specifické pro společnost Microsoft**

Předá do Optimalizátoru nápovědu.

## <a name="syntax"></a>Syntaxe

```C
__assume(
   expression
)
```

### <a name="parameters"></a>Parametry

*vyjádření*\
Libovolný výraz, který se předpokládá pro vyhodnocení na hodnotu true.

## <a name="remarks"></a>Poznámky

Optimalizátor předpokládá, že podmínka reprezentovaná `expression` je pravdivá v místě, kde se klíčové slovo zobrazí a zůstává true, dokud `expression` není změněno (například přiřazením proměnné). Selektivní použití pomocných parametrů předaných Optimalizátoru `__assume` může zlepšit optimalizaci.

Pokud je `__assume(0)`příkaz zapsán jako odpor (výraz, který vždy vyhodnocuje jako NEPRAVDA), je vždy považován za. `__assume` Pokud se kód nechová podle očekávání, ujistěte se, že `expression` jste definovali platné a pravdivé, jak je popsáno výše. Další informace o očekávaném `__assume(0)` chování najdete v pozdějších komentářích.

> [!WARNING]
>  Program nesmí obsahovat neplatný `__assume` příkaz pro dosažitelnou cestu. Pokud kompilátor může dosáhnout neplatného `__assume` příkazu, program může způsobit nepředvídatelné a potenciálně nebezpečné chování.

`__assume`není originálním vnitřním. Nemusí být deklarován jako funkce a nelze jej použít v `#pragma intrinsic` direktivě. I když není generován žádný kód, je ovlivněn kód vygenerovaný optimalizátorem.

Použijte `__assume` v [Assert](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) pouze v případě, že je kontrolní výraz neobnovitelný. Nepoužívejte `__assume` v kontrolním výrazu, pro který máte následný kód pro obnovení chyb, protože kompilátor může optimalizovat kód pro zpracování chyb.

`__assume(0)` Příkaz je zvláštní případ. Použijte `__assume(0)` k označení cesty kódu, ke které nelze získat přístup. Následující příklad ukazuje, jak použít `__assume(0)` k označení toho, že výchozí případ příkazu switch není dostupný. To ukazuje Nejběžnější použití `__assume(0)`.

Z důvodu kompatibility s předchozími verzemi je **_assume** synonymem pro **__assume** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
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

Použití `__assume(0)` nástroje oznamuje Optimalizátoru, že výchozí velikost písmen není dostupná. Příklad ukazuje, že programátor ví, že jediné možné vstupy pro `p` budou 1 nebo 2. Pokud je předána jiná hodnota pro `p`, program bude neplatný a způsobí nepředvídatelné chování.

V důsledku `__assume(0)` příkazu Kompilátor negeneruje kód pro testování, zda `p` má hodnotu, která není reprezentovaná v příkazu case. Aby to fungovalo, `__assume(0)` musí být příkaz prvním příkazem v těle výchozího případu.

Vzhledem k tomu, že kompilátor generuje `__assume`kód založený na, tento kód nemusí fungovat správně, pokud je `__assume` výraz uvnitř příkazu v době běhu false. Pokud si nejste jistí, že výraz bude vždy true v době běhu, můžete použít `assert` funkci k ochraně kódu.

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Toto použití `assert` bohužel brání kompilátoru v provedení optimalizace s výchozími případy, které byly popsány dříve v tomto dokumentu. Alternativně můžete použít samostatné makro, a to následujícím způsobem.

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
