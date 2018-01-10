---
title: "Import volání funkcí pomocí deklarace __declspec(dllimport) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __declspec
- dllimport
dev_langs: C++
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5553bd5e9999a4737dc258358402eb71269b9c40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Import volání funkcí pomocí deklarace __declspec(dllimport)
Následující příklad kódu ukazuje, jak používat **_declspec(dllimport)** Import volání funkcí z knihovny DLL do aplikace. Předpokládáme, že `func1` je funkce, která se nachází v knihovně DLL oddělené od souboru .exe, který obsahuje **hlavní** funkce.  
  
 Bez **deklarace __declspec(dllimport)**, daný tento kód:  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 kompilátor vygeneruje kód, který vypadá takto:  
  
```  
call func1  
```  
  
 a linkeru převede volání do přibližně takto:  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 Pokud `func1` existuje v jiné knihovně DLL linkeru nelze vyřešit přímo protože nemá žádný způsob, jak zjistit, jaká je adresa `func1` je. V prostředích 16bitové přidá linkeru tuto adresu kód v souboru .exe, který by zavaděč za běhu se správnou adresou v seznamu. V prostředích 32bitové a 64bitové verze generuje linkeru převodu, které zná adresu. V prostředí s 32-bit jinou bitovou šířku vypadá takto:  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 Zde `imp_func1` adresa pro `func1` slot v tabulce importovaných adres souboru .exe. Všechny adresy jsou tedy známy linkeru. Zavaděč má jenom k aktualizaci tabulky adres importovat soubor .exe při načítání, aby vše správně fungovat.  
  
 Proto pomocí **deklarace __declspec(dllimport)** je lepší, protože linkeru negeneruje převodu, pokud není potřeba. Převody zvětšit kód (v systémech RISC, může být několik pokyny) a může snížit výkon mezipaměti. Pokud jste, že funkce je v knihovně DLL oznámení kompilátoru, to může generovat nepřímé volání za vás.  
  
 Proto nyní tento kód:  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 generuje tento pokyn:  
  
```  
call DWORD PTR __imp_func1  
```  
  
 K dispozici není žádná převodu a ne `jmp` pokyn, aby kód je menší a rychlejší.  
  
 Na druhé straně pro volání funkcí uvnitř knihovny DLL, které nechcete muset použít nepřímé volání. Už víte, adresu funkce. Protože jsou náročné na načíst a uložit na adresu funkce před nepřímé volání na čas a místa, přímé volání je vždy rychlejší a menší. Chcete použít **deklarace __declspec(dllimport)** při volání funkcí knihovny DLL mimo knihovnu DLL, sám sebe. Nepoužívejte **deklarace __declspec(dllimport)** na funkcích uvnitř knihovny DLL při vytváření této knihovny DLL.  
  
## <a name="see-also"></a>Viz také  
 [Import do aplikace](../build/importing-into-an-application.md)