---
title: Důležité informace k zápisu kódu prologu epilogu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd3d63ed06ee07943263e6f8a59bb9fceea4d99d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="considerations-when-writing-prologepilog-code"></a>Důležité informace k zápisu kódu prologu/epilogu
**Konkrétní Microsoft**  
  
 Před psaním vlastních sekvencí kódu prologu a epilogu je zapotřebí porozumět rozložení rámce zásobníku. Je také užitečné vědět, jak používat **__local_size –** předdefinované konstanta.  
  
##  <a name="_clang_c_stack_frame_layout"></a> Rozložení rámce zásobníku C  
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
  
##  <a name="_clang_the___local_size_constant"></a> __Local_size – konstanta  
 Kompilátor poskytuje konstantu, **__local_size –**, pro použití v vloženého assembleru blok kódu prologu funkce. Tato konstanta se používá k přidělení místa pro místní proměnné v rámci zásobníku ve vlastním kódu prologu.  
  
 Kompilátor určuje hodnota **__local_size –**. Hodnotou je celkový počet bajtů všech místních proměnných definovaných uživatelem a dočasných proměnných generovaných kompilátorem. **__Local_size –** lze použít pouze jako okamžitou operand; ji nelze použít ve výrazu. Hodnota této konstanty nesmí být v kódu měněna nebo předefinována. Příklad:  
  
```  
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov      eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 Následující příklad holé funkce obsahující vlastní prolog a epilog pořadí používá **__local_size –** v prologu pořadí:  
  
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
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Holé funkce](../c-language/naked-functions.md)