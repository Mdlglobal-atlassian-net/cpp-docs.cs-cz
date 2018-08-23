---
title: code_seg | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs:
- C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 052e9a55d443fa263ecf8443c9e3933baeb1f3b8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465312"
---
# <a name="codeseg"></a>code_seg
Určuje textový segment, kde jsou funkce uloženy v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 
**Code_seg** – Direktiva pragma neřídí umístění objektového kódu generovaného pro instancované šablony ani kódu generovaného implicitně kompilátorem, například zvláštní členské funkce. Doporučujeme použít [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) místo toho atribut, protože s ním můžete ovládat umístění celého objektového kódu. To zahrnuje kód generovaný kompilátorem.  
  
A *segmentu* soubor v .obj je pojmenovaný blok dat, který je načten do paměti jako celek. A *textový segment* je segment, který obsahuje spustitelný kód. V tomto článku se podmínky *segmentu* a *části* zaměňují.  
  
**Code_seg** – Direktiva pragma instruuje kompilátor, aby uvedl veškerý následný objektový kód z převodu jednotky do textového segmentu text s názvem *segment-name*. Ve výchozím nastavení se textový segment použitý v souboru .obj nazývá .text.  
  
A **code_seg** – Direktiva pragma bez parametrů obnoví název textového segmentu pro následný objektový kód na .text.  
  
*push* (volitelné)  
Vloží záznam do zásobníku vnitřního kompilátoru. A *nabízených* může mít *identifikátor* a *segment-name*.  
  
*POP* (volitelné)  
Odstraní nejvyšší záznam z vnitřního zásobníku kompilátoru.  
  
*identifikátor* (volitelné)  
Při použití s *nabízených*, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. Při použití s *pop*, vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic nevezme.  
  
*identifikátor* vyjmout několik záznamů pro odebrání pouze s jedním *pop* příkazu.  
  
"*segment-name*" (volitelné)  
Název segmentu Při použití s *pop*, je zásobník odebrán a *segment-name* stane názvem textového segmentu.  
  
"*segmentu třídy*" (volitelné)  
Ignorováno, ale zahrnuto pro kompatibilitu s verzemi jazyka C++ před verzí 2.0.  
  
Můžete použít [DUMPBIN. Soubor EXE](../build/reference/dumpbin-command-line.md) aplikace k zobrazení souborů obj. Součástí sady Visual Studio jsou verze DUMPBIN pro každou podporovanou cílovou architekturu.  
  
## <a name="example"></a>Příklad  

Tento příklad ukazuje způsob použití **code_seg** – Direktiva pragma pro ovládací prvek, kde objektového kódu:  
  
```cpp  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
Seznam názvů, které by neměly být použít k vytvoření oddílu, naleznete v tématu [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
Můžete také určit oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a proměnné const ([const_seg](../preprocessor/const-seg.md)).  
  
## <a name="see-also"></a>Viz také  
 
[code_seg (__declspec)](../cpp/code-seg-declspec.md)   
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)