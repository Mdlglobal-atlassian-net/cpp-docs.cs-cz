---
title: Důležité informace k zápisu kódu prologu/epilogu
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: cda6a6c82efcf30a916aced121024095d7ce8138
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337101"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Důležité informace k zápisu kódu prologu/epilogu

**Specifické pro Microsoft**

Před zápisem vlastní prolog a epilog sekvence kódu, je důležité pochopit, jak je rozložen rámec zásobníku. Je také užitečné vědět, jak `__LOCAL_SIZE` používat symbol.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Rozložení rámce zásobníku

Tento příklad ukazuje standardní kód prologu, který se může vyskytnout v 32bitové funkci:

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

Proměnná `localbytes` představuje počet bajtů zásobníku potřebných pro místní proměnné a proměnná `<registers>` je zástupný symbol představující seznam registrů, které mají být uloženy do zásobníku. Po vložení registrů lze do zásobníku uložit libovolná jiná vhodná data. Následující výpis ukazuje odpovídající kód epilogu:

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

Zásobník roste vždy směrem dolů (od vysokých po nízké adresy paměti). Základní ukazatel (`ebp`) ukazuje na vloženou hodnotu proměnné `ebp`. Oblast místních obyvatel `ebp-4`začíná na . Chcete-li přistoupit k místním proměnným, vypočítejte posun vůči adrese `ebp` odečtením příslušné hodnoty od adresy `ebp`.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a>__LOCAL_SIZE

Kompilátor poskytuje symbol `__LOCAL_SIZE`, pro použití v inline assembler bloku funkce prolog kód. Tento symbol se používá k přidělení místa pro místní proměnné v rámci zásobníku ve vlastním kódu prologu.

Kompilátor určuje hodnotu `__LOCAL_SIZE`. Jeho hodnota je celkový počet bajtů všech uživatelem definovaných místních proměnných a dočasných proměnných generovaných kompilátorem. `__LOCAL_SIZE`lze použít pouze jako okamžitý operand; nelze jej použít ve výrazu. Hodnotu tohoto symbolu nesmíte měnit ani předefinovat. Příklad:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

Následující příklad funkce naked obsahující vlastní sekvence prologu a `__LOCAL_SIZE` epilogu používá symbol v sekvenci prologu:

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Volání holé funkce](../cpp/naked-function-calls.md)
