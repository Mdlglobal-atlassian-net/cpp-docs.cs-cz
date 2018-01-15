---
title: "bss_seg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dd1e24127129ef833cfd4906085eabbf1e5c380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bssseg"></a>bss_seg
Určuje, kde, neinicializovaného proměnné jsou uloženy v souboru .obj segmentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubory obj lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. Segment výchozí v souboru .obj Neinicializovaný dat je .bss. V některých případech použití **bss_seg –** může urychlit načíst časy seskupením Neinicializovaný data do oddílů.  
  
 **bss_seg –** bez parametrů obnoví na .bss segmentu.  
  
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
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 Můžete také určit oddíly pro inicializovaného dat ([data_seg](../preprocessor/data-seg.md)), funkce ([code_seg](../preprocessor/code-seg.md)) a const proměnné ([const_seg –](../preprocessor/const-seg.md)).  
  
 Data přidělen s použitím **bss_seg –** – Direktiva pragma nezachovává žádné informace o jeho umístění.  
  
 V tématu [/SECTION](../build/reference/section-specify-section-attributes.md) pro seznam názvů byste neměli používat při vytváření oddílu.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)