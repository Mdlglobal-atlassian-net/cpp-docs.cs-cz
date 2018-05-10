---
title: data_seg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs:
- C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a463d966c681557525bb9512762731c01a7ce30
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="dataseg"></a>data_seg
Určuje, kde inicializovaného proměnné jsou uloženy v souboru .obj datového segmentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Význam podmínky *segment* a *části* se zaměňovat v tomto tématu.  
  
 Soubory OBJ lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. .Data – je výchozím segmentem v souboru .obj inicializovaného proměnné. Proměnné, které Neinicializovaný jsou považovány za inicializovat na hodnotu nula a jsou uložené v .bss.  
  
 **data_seg –** obnoví segmentu .data – bez parametrů.  
  
 **nabízená**(volitelné)  
 Vloží záznam do zásobníku vnitřního kompilátoru. A **nabízené** může mít *identifikátor* a *název segmentu*.  
  
 **POP** (volitelné)  
 Odstraní nejvyšší záznam z vnitřního zásobníku kompilátoru.  
  
 *identifikátor* (volitelné)  
 Při použití s **nabízené**, přiřadí název záznamu v zásobníku vnitřní kompilátoru. Při použití s **pop**, POP záznamy ze zásobníku vnitřní, dokud *identifikátor* odebrána; Pokud *identifikátor* nebyl nalezen v interní zásobníku, nic se odebrány.  
  
 *identifikátor* umožňuje více záznamů, chcete-li být odebrány s jedním **pop** příkaz.  
  
 *"název segmentu"*(volitelné)  
 Název segmentu Při použití s **pop**, je odebrány zásobníku a *název segmentu* stane názvem active segmentu.  
  
 *"segment třídy"* (volitelné)  
 Zahrnuto z důvodu kompatibility s jazykem C++ starším než verze 2.0. Ignorováno.  
  
## <a name="example"></a>Příklad  
  
```  
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 Data přidělen s použitím **data_seg** nezachovává žádné informace o jeho umístění.  
  
 V tématu [/SECTION](../build/reference/section-specify-section-attributes.md) pro seznam názvů byste neměli používat při vytváření oddílu.  
  
 Můžete také určit oddíly pro const proměnné ([const_seg –](../preprocessor/const-seg.md)), Neinicializovaný dat ([bss_seg –](../preprocessor/bss-seg.md)) a funkce ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)