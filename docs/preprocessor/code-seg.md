---
title: code_seg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs: C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91834205187ecfa3c56c04aaac9cd0a2d25b49fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="codeseg"></a>code_seg
Určuje textový segment, kde jsou funkce uloženy v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 `code_seg` – Direktiva pragma neřídí umístění objektu kód, který vygenerovala vytvořenou instanci šablon, ani kód vygenerovaný kompilátor implicitně – například speciální členské funkce. Doporučujeme vám, že používáte [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) atribut místo, protože můžete ovládat umístění všech kód objektu. To zahrnuje kód generovaný kompilátorem.  
  
 A *segment* v .obj je soubor s názvem blok dat, který je načten do paměti jako jednotku. A *text segmentu* je segment, který obsahuje spustitelný kód. V tomto článku podmínky *segment* a *části* používají zcela zaměnitelným významem.  
  
 `code_seg` – Direktiva pragma říká kompilátoru převést všechny následné objekt kód z jednotky překladu do textu segment s názvem `segment-name`. Ve výchozím nastavení se textový segment použitý v souboru .obj nazývá .text.  
  
 A `code_seg` – Direktiva pragma bez parametrů obnoví názvu text segmentu pro kód následné objektu na text.  
  
 **Push** (volitelné)  
 Vloží záznam do zásobníku vnitřního kompilátoru. A **nabízené** může mít `identifier` a `segment-name`.  
  
 **POP** (volitelné)  
 Odstraní nejvyšší záznam z vnitřního zásobníku kompilátoru.  
  
 `identifier`(volitelné)  
 Při použití s **nabízené**, přiřadí název záznamu v zásobníku vnitřní kompilátoru. Při použití s **pop**, POP záznamy ze zásobníku vnitřní, dokud `identifier` odebrána; Pokud `identifier` nebyl nalezen v interní zásobníku, nic se odebrány.  
  
 `identifier`umožňuje více záznamů, chcete-li být odebrány s právě jedním **pop** příkaz.  
  
 "`segment-name`" (volitelné)  
 Název segmentu Při použití s **pop**, je odebrány zásobníku a `segment-name` stane názvem active text segmentu.  
  
 "`segment-class`" (volitelné)  
 Ignorováno, ale zahrnuto pro kompatibilitu s verzemi jazyka C++ před verzí 2.0.  
  
 Můžete použít [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) aplikace zobrazíte soubory .obj. Součástí jsou verze DUMPBIN pro každou architekturu podporovaný cíl [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití `code_seg` – Direktiva pragma řídit, kde je kód objektu put:  
  
```  
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
  
 Seznam názvů, které by neměl být použít k vytvoření oddílu najdete v tématu [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 Můžete také určit oddíly pro inicializovaného dat ([data_seg](../preprocessor/data-seg.md)), Neinicializovaný dat ([bss_seg –](../preprocessor/bss-seg.md)) a const proměnné ([const_seg –](../preprocessor/const-seg.md)).  
  
## <a name="see-also"></a>Viz také  
 [code_seg (__declspec)](../cpp/code-seg-declspec.md)   
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)