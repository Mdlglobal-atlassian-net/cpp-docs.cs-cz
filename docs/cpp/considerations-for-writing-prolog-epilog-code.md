---
title: Předpoklady pro zápis kódu prologu a epilogu
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: a598ddbdd1b5f91c97e32905202e264b444c05d0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988698"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Důležité informace k zápisu kódu prologu/epilogu

**Specifické pro společnost Microsoft**

Před zápisem vlastních sekvencí kódu prologu a epilogu je důležité pochopit, jak je rámec zásobníku rozložen. Je také užitečné zjistit, jak používat symbol `__LOCAL_SIZE`.

##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Rozložení rámce zásobníku

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

Zásobník roste vždy směrem dolů (od vysokých po nízké adresy paměti). Základní ukazatel (`ebp`) ukazuje na vloženou hodnotu proměnné `ebp`. Oblast místních hodnot začíná na `ebp-4`. Chcete-li přistoupit k místním proměnným, vypočítejte posun vůči adrese `ebp` odečtením příslušné hodnoty od adresy `ebp`.

##  <a name="_pluslang___local_size"></a>__LOCAL_SIZE

Kompilátor poskytuje symbol, `__LOCAL_SIZE`pro použití v vloženém bloku assembleru kódu prologu funkce. Tento symbol slouží k přidělení prostoru pro lokální proměnné v bloku zásobníku v kódu vlastního prologu.

Kompilátor Určuje hodnotu `__LOCAL_SIZE`. Jeho hodnota je celkový počet bajtů všech místních proměnných definovaných uživatelem a dočasných proměnných generovaných kompilátorem. `__LOCAL_SIZE` lze použít pouze jako okamžitý operand; nedá se použít ve výrazu. Hodnotu tohoto symbolu nesmíte změnit ani předefinovat. Příklad:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

Následující příklad holé funkce obsahující vlastní sekvenci prologu a epilog používá symbol `__LOCAL_SIZE` v sekvenci prologu:

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Volání holé funkce](../cpp/naked-function-calls.md)
