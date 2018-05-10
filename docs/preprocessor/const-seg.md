---
title: const_seg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 984dc392b6ffa51d662d3ab56b1c0dc0dbc92233
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="constseg"></a>const_seg
Určuje segment kde [const](../cpp/const-cpp.md) proměnné jsou uloženy v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Význam podmínky *segment* a *části* se zaměňovat v tomto tématu.  
  
 Soubory OBJ lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. Výchozí segmentu v souboru .obj `const` proměnné je .rdata. Některé `const` proměnné, jako je například skalárních hodnot, jsou automaticky vložená do datového proudu kódu. Vložený kód se v segmentu .rdata nezobrazí.  
  
 Definování vyžadující dynamické inicializace v objektu `const_seg` výsledkem nedefinované chování.  
  
 `#pragma const_seg` bez parametrů obnoví segmentu na .rdata.  
  
 `push` (volitelné)  
 Vloží záznam do zásobníku vnitřního kompilátoru. A `push` může mít `identifier` a `segment-name`.  
  
 `pop` (volitelné)  
 Odstraní nejvyšší záznam z vnitřního zásobníku kompilátoru.  
  
 `identifier` (volitelné)  
 Při použití s `push`, přiřadí název záznamu v zásobníku vnitřní kompilátoru. Při použití s `pop`, POP záznamy ze zásobníku vnitřní, dokud `identifier` odebrána; Pokud `identifier` nebyl nalezen v interní zásobníku, nic se odebrány.  
  
 Pomocí `identifier` umožňuje více záznamů, chcete-li být odebrány s jedním `pop` příkaz.  
  
 "`segment-name`" (volitelné)  
 Název segmentu Při použití s `pop`, je odebrány zásobníku a `segment-name` stane názvem active segmentu.  
  
 "`segment-class`" (volitelné)  
 Zahrnuto z důvodu kompatibility s jazykem C++ starším než verze 2.0. Ignorováno.  
  
## <a name="example"></a>Příklad  
  
```  
// pragma_directive_const_seg.cpp  
// compile with: /EHsc  
#include <iostream>  
  
const int i = 7;               // inlined, not stored in .rdata  
const char sz1[]= "test1";     // stored in .rdata  
  
#pragma const_seg(".my_data1")  
const char sz2[]= "test2";     // stored in .my_data1  
  
#pragma const_seg(push, stack1, ".my_data2")  
const char sz3[]= "test3";     // stored in .my_data2  
  
#pragma const_seg(pop, stack1) // pop stack1 from stack  
const char sz4[]= "test4";     // stored in .my_data1  
  
int main() {  
    using namespace std;  
   // const data must be referenced to be put in .obj  
   cout << sz1 << endl;  
   cout << sz2 << endl;  
   cout << sz3 << endl;  
   cout << sz4 << endl;  
}  
```  
  
```Output  
test1  
test2  
test3  
test4  
```  
  
## <a name="comments"></a>Komentáře  
 V tématu [/SECTION](../build/reference/section-specify-section-attributes.md) pro seznam názvů byste neměli používat při vytváření oddílu.  
  
 Můžete také určit oddíly pro inicializovaného dat ([data_seg](../preprocessor/data-seg.md)), Neinicializovaný dat ([bss_seg –](../preprocessor/bss-seg.md)) a funkce ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)