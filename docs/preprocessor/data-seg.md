---
title: data_seg | Dokumentace Microsoftu
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
ms.openlocfilehash: b1be97919f0f5b55d6e63eca8e59eb15e8ef9dff
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464900"
---
# <a name="dataseg"></a>data_seg
Určuje datový segment inicializované proměnné, kde jsou uloženy v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky 

Významy pojmů *segmentu* a *části* jsou v tomto tématu zaměnitelné.  
  
Soubory OBJ lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. .Data je výchozím segmentem v souboru .obj inicializované proměnných. Proměnné, které neinicializované jsou považovány za inicializovány na nulu a jsou uloženy v .bss.  
  
**data_seg** bez parametrů obnoví nastavení segmentu na .data.  
  
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
  
Data Alokovaná pomocí **data_seg** nezachovává žádné informace o jeho umístění.  
  
Zobrazit [/SECTION](../build/reference/section-specify-section-attributes.md) seznam názvů byste neměli používat při tvorbě oddílu.  
  
Můžete také určit oddíly pro proměnné const ([const_seg](../preprocessor/const-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a funkce ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)