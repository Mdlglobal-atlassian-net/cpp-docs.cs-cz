---
title: __asm | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __asm
- __asm_cpp
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: df1beb4353a537d9e22147fd8dcb79810632c111
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asm"></a>__asm
**Konkrétní Microsoft**  
  
 `__asm` – Klíčové slovo vyvolá vloženého assembleru a může vyskytovat kdekoli je právní příkaz jazyka C nebo C++. Se nemůže objevit samostatně. Musí být následováno instrukci sestavení skupinu instrukce uzavřené do složených závorek, nebo v každém, prázdný pár složené závorky. Termín "`__asm` bloku" zde označují jakýkoliv pokyn nebo skupiny pokynů, zda v závorkách.  
  
> [!NOTE]
>  Podpora jazyka Visual C++ pro standardní C++ `asm` – klíčové slovo je omezená na to, že kompilátor nevygeneruje chybu na klíčové slovo. Však `asm` bloku nevygeneruje žádný kód smysluplný. Použití `__asm` místo `asm`.  
  
 Syntaxe:  
  
 __asm *sestavení instrukce* [;]  
  
 __asm { *seznam sestavení instrukce* } [;]  
  
## <a name="grammar"></a>Gramatika  
 `__asm`  `assembly-instruction`  `;`OPT  
  
 `__asm {`  `assembly-instruction-list`  `};`OPT  
  
 *seznam sestavení instrukce*:  
 `assembly-instruction``;`opt  
  
 `assembly-instruction``;` `assembly-instruction-list` `;`opt  
  
 Pokud se použije bez složené závorky `__asm` – klíčové slovo znamená, že je zbytek řádku příkazu jazyka sestavení. Pokud používají složené závorky, znamená to, že každý řádek mezi složenými závorkami je příkazem jazyka sestavení. Pro kompatibilitu s předchozími verzemi `_asm` se jedná o synonymum `__asm`.  
  
 Vzhledem k tomu `__asm` – klíčové slovo je příkaz oddělovač, sestavení pokynů můžete umístit na stejný řádek.  
  
 Před Visual C++ 2005, pokyn  
  
```  
__asm int 3  
```  
  
 nativní kód vygenerován, když kompilujete s nezpůsobila **/CLR**; kompilátor přeložit pokyn k přerušení instrukci CLR.  
  
 `__asm int 3`Nyní výsledky při generování nativní kód pro funkci. Pokud chcete, aby funkce, která se způsobit přerušení v kódu a pokud chcete tuto funkci zkompilovány do MSIL, použijte [__debugbreak –](../../intrinsics/debugbreak.md).  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu je jednoduchý `__asm` bloku uzavřené do složených závorek:  
  
```  
__asm {  
   mov al, 2  
   mov dx, 0xD007  
   out dx, al  
}  
```  
  
 Alternativně můžete umístit `__asm` před každou instrukci sestavení:  
  
```  
__asm mov al, 2  
__asm mov dx, 0xD007  
__asm out dx, al  
```  
  
 Protože `__asm` – klíčové slovo je příkaz oddělovač, přepnete sestavení pokyny na stejném řádku:  
  
```  
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al  
```  
  
 Všechny tři příklady generovat stejný kód, ale styl první (obklopuje `__asm` blokovat v závorkách) má několik výhod. Složené závorky jasně oddělené kódu sestavení z kódu jazyka C nebo C++ a vyhnout se zbytečně opakování `__asm` – klíčové slovo. Složené závorky, můžete také zabránit nejednoznačnosti. Pokud chcete blokovat příkaz jazyka C nebo C++ na stejném řádku jako `__asm` bloku, blok je nutné uzavřít do složených závorek. Kompilátor bez složené závorky, nemůže určit, kde sestavení kódu zastaví a příkazy jazyka C nebo C++ začít. Nakonec protože text do složených závorek má stejný formát jako běžného textu MASM, můžete snadno vyjmout a vložit text ze stávající MASM zdrojové soubory.  
  
 Na rozdíl od složené závorky jazyka C a C++, složené závorky obklopuje `__asm` bloku neovlivňuje obor proměnné. Můžete také vnořovat `__asm` bloky; vnoření nemá vliv na obor proměnné.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../../cpp/keywords-cpp.md)   
 [Vložený Assembler](../../assembler/inline/inline-assembler.md)