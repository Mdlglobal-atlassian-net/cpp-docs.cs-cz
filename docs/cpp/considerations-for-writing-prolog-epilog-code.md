---
title: "Důležité informace k zápisu kódu prologu epilogu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31cc8b71a05198fcc5cca62011fe8d88a668adbe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="considerations-for-writing-prologepilog-code"></a>Důležité informace k zápisu kódu prologu/epilogu
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Před psaním vlastních sekvencí kódu prologu a epilogu je zapotřebí porozumět rozložení rámce zásobníku. Je také užitečné vědět, jak používat **__local_size –** symbol.  
  
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
  
 Zásobník roste vždy směrem dolů (od vysokých po nízké adresy paměti). Základní ukazatel (`ebp`) ukazuje na vloženou hodnotu proměnné `ebp`. Místní hodnoty oblasti začíná na `ebp-4`. Chcete-li přistoupit k místním proměnným, vypočítejte posun vůči adrese `ebp` odečtením příslušné hodnoty od adresy `ebp`.  
  
##  <a name="_pluslang___local_size"></a>__LOCAL_SIZE –  
 Kompilátor poskytuje symbol, **__local_size –**, pro použití v vloženého assembleru blok kódu prologu funkce. Tento symbol se používá k přidělení místa pro místní proměnné na rámec zásobníku v kódu prologu vlastní.  
  
 Kompilátor určuje hodnota **__local_size –**. Její hodnota je celkový počet bajtů všech uživatelem definované místní proměnné a generované kompilátorem dočasné proměnné. **__Local_size –** lze použít pouze jako okamžitou operand; ji nelze použít ve výrazu. Nesmí změnit nebo znovu definovat hodnotu tento symbol. Příklad:  
  
```  
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov        eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 Následující příklad holé funkce obsahující vlastní prolog a epilog pořadí používá **__local_size –** symbol v prologu pořadí:  
  
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
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Volání holé funkce](../cpp/naked-function-calls.md)