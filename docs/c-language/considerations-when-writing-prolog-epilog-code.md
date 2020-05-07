---
title: Pokyny k zápisu kódu prologu a epilogu
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: e1559c75808a72cd3f9674399bec036cf392b44f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334585"
---
# <a name="considerations-when-writing-prologepilog-code"></a>Důležité informace k zápisu kódu prologu/epilogu

**Specifické pro Microsoft**

Před zápisem vlastních sekvencí kódu prologu a epilogu je důležité pochopit, jak je rámec zásobníku rozložen. Je také užitečné znát způsob použití **__LOCAL_SIZE** předdefinované konstanty.

## <a name="cstack-frame-layout"></a><a name="_clang_c_stack_frame_layout"></a>Rozložení rámce CStack

Tento příklad ukazuje standardní kód prologu, který se může vyskytnout v 32bitové funkci:

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

Proměnná `localbytes` představuje počet bajtů zásobníku potřebných pro místní proměnné a proměnná `registers` je zástupný symbol představující seznam registrů, které mají být uloženy do zásobníku. Po vložení registrů lze do zásobníku uložit libovolná jiná vhodná data. Následující výpis ukazuje odpovídající kód epilogu:

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

Zásobník roste vždy směrem dolů (od vysokých po nízké adresy paměti). Základní ukazatel (`ebp`) ukazuje na vloženou hodnotu proměnné `ebp`. Oblast místních proměnných začíná na adrese `ebp-2`. Chcete-li přistoupit k místním proměnným, vypočítejte posun vůči adrese `ebp` odečtením příslušné hodnoty od adresy `ebp`.

## <a name="the-__local_size-constant"></a><a name="_clang_the___local_size_constant"></a>__LOCAL_SIZE konstanta

Kompilátor poskytuje konstantu, **__LOCAL_SIZE**pro použití v vloženém bloku assembleru kódu prologu funkce. Tato konstanta se používá k přidělení místa pro místní proměnné v rámci zásobníku ve vlastním kódu prologu.

Kompilátor Určuje hodnotu **__LOCAL_SIZE**. Hodnotou je celkový počet bajtů všech místních proměnných definovaných uživatelem a dočasných proměnných generovaných kompilátorem. **__LOCAL_SIZE** lze použít pouze jako okamžitý operand; nedá se použít ve výrazu. Hodnota této konstanty nesmí být v kódu měněna nebo předefinována. Příklad:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

Následující příklad holé funkce obsahující vlastní sekvence prologu a epilog používá **__LOCAL_SIZE** v sekvenci prologu:

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Holé funkce](../c-language/naked-functions.md)
