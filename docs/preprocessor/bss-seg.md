---
title: bss_seg | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08304a42b961f93b7d9e4e6e644e1514e34eb335
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464797"
---
# <a name="bssseg"></a>bss_seg
Určuje segment neinicializované proměnné, kde jsou uloženy v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 
Soubory obj lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. Výchozí segment v souboru obj neinicializovaná data je .bss. V některých případech použití **bss_seg** můžete urychlit načítání časy seskupením neinicializovaná data do jednoho oddílu.  
  
**bss_seg** bez parametrů obnoví nastavení segmentu na .bss.  
  
*push* (volitelné)  
Vloží záznam do zásobníku vnitřního kompilátoru. A *nabízených* může mít *identifikátor* a *segment-name*.  
  
*POP* (volitelné)  
Odstraní nejvyšší záznam z vnitřního zásobníku kompilátoru.  
  
*identifikátor* (volitelné)  
Při použití s *nabízených*, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. Při použití s *pop*, vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic nevezme.  
  
*identifikátor* vyjmout několik záznamů lze jedním z jedné *pop* příkazu.  
  
*"segment-name"*(volitelné)  
Název segmentu Při použití s *pop*, je zásobník odebrán a *segment-name* stane aktivním názvem segmentu.  
  
*"segmentu třídy"* (volitelné)  
Zahrnuto z důvodu kompatibility s jazykem C++ starším než verze 2.0. Ignorováno.  
  
## <a name="example"></a>Příklad  
  
```cpp  
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
  
Můžete také určit oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), funkce ([code_seg](../preprocessor/code-seg.md)) a proměnné const ([const_seg](../preprocessor/const-seg.md)).  
  
Data Alokovaná pomocí **bss_seg** – Direktiva pragma nezachovává žádné informace o jeho umístění.  
  
Zobrazit [/SECTION](../build/reference/section-specify-section-attributes.md) seznam názvů byste neměli používat při tvorbě oddílu.  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)