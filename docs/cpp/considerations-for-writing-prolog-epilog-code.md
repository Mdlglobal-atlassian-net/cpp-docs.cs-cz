---
title: Důležité informace k zápisu kódu prologu / epilogu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b581a57db7e66d1547ffd90509c62353d78d478b
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464113"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Důležité informace k zápisu kódu prologu/epilogu
 **Specifické pro Microsoft**  
 Před psaním vlastních sekvencí kódu prologu a epilogu je zapotřebí porozumět rozložení rámce zásobníku. Také je užitečné vědět, jak používat `__LOCAL_SIZE` symbol.  
  
##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a> Rozložení rámce zásobníku  
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
  
 Zásobník roste vždy směrem dolů (od vysokých po nízké adresy paměti). Základní ukazatel (`ebp`) ukazuje na vloženou hodnotu proměnné `ebp`. Oblast místních hodnot začíná u `ebp-4`. Chcete-li přistoupit k místním proměnným, vypočítejte posun vůči adrese `ebp` odečtením příslušné hodnoty od adresy `ebp`.  
  
##  <a name="_pluslang___local_size"></a> __LOCAL_SIZE  
 Kompilátor poskytuje symbol, `__LOCAL_SIZE`, pro použití ve vloženém bloku assembleru daného kódu prologu funkce. Tento symbol se používá k přidělení místa pro místní proměnné v rámci zásobníku ve vlastním kódu prologu.  
  
 Kompilátor Určuje hodnotu `__LOCAL_SIZE`. Jeho hodnota je celkový počet bajtů všech místních proměnných definovaných uživateli a dočasných proměnných generovaných kompilátoru. `__LOCAL_SIZE` lze použít pouze jako přímý operand. nelze použít ve výrazu. Nesmí měnit nebo znovu definovat hodnotu tohoto symbolu. Příklad:  
  
```  
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov        eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 Následující příklad neviditelné funkce obsahující vlastní sekvence prologu a epilogu pořadí použití `__LOCAL_SIZE` symbolu v sekvenci prologu:  
  
```  
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
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Volání holé funkce](../cpp/naked-function-calls.md)