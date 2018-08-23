---
title: const_seg | Dokumentace Microsoftu
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
ms.openlocfilehash: a3081837cc4516750f8c2c0d75cfc37eef208f9d
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465003"
---
# <a name="constseg"></a>const_seg
Určuje segment kde [const](../cpp/const-cpp.md) proměnné, které jsou uloženy v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 
Významy pojmů *segmentu* a *části* jsou v tomto tématu zaměnitelné.  
  
Soubory OBJ lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. Výchozím segmentem v souboru obj `const` proměnné je segment .rdata. Některé `const` proměnných, například skaláry, jsou automaticky vloženy do kódu. Vložený kód se v segmentu .rdata nezobrazí.  
  
Definování vyžadující dynamická inicializace v objektu `const_seg` způsobí nedefinované chování.  
  
`#pragma const_seg` bez parametrů obnoví segment .rdata.  
  
*push* (volitelné)  
Vloží záznam do zásobníku vnitřního kompilátoru. A *nabízených* může mít *identifikátor* a *segment-name*.  
  
*POP* (volitelné)  
Odstraní nejvyšší záznam z vnitřního zásobníku kompilátoru.  
  
*identifikátor* (volitelné)  
Při použití s *nabízených*, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. Při použití s *pop*, vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic nevezme.  
  
Pomocí *identifikátor* vyjmout několik záznamů lze jedním z jedné *pop* příkazu.  
  
"*segment-name*" (volitelné)  
Název segmentu Při použití s *pop*, je zásobník odebrán a *segment-name* stane aktivním názvem segmentu.  
  
"*segmentu třídy*" (volitelné)  
Zahrnuto z důvodu kompatibility s jazykem C++ starším než verze 2.0. Ignorováno.  
  
## <a name="example"></a>Příklad  
  
```cpp  
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
 
Zobrazit [/SECTION](../build/reference/section-specify-section-attributes.md) seznam názvů byste neměli používat při tvorbě oddílu.  
  
Můžete také určit oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a funkce ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)