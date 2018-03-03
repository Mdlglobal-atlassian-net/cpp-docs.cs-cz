---
title: __stdcall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __stdcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec45f93331178f62799fb826ff31dfb6e66c3337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stdcall"></a>__stdcall
**Konkrétní Microsoft**  
  
 `__stdcall` Konvence volání se používá k volání funkcí rozhraní API Win32. Volaného vyčistí zásobníku, takže díky kompilátor **vararg** funkce `__cdecl`. Funkce, které konvence volání musí prototyp funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
return-type __stdcall function-name[(argument-list)]  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující seznam ukazuje implementaci této konvence volání.  
  
|Prvek|Implementace|  
|-------------|--------------------|  
|Pořadí předávání argumentů|Zprava doleva.|  
|Konvence předávání argumentů|Podle hodnoty Pokud na ukazatel nebo odkaz na typ je předán.|  
|Odpovědnost za údržbu zásobníku|Volá vlastní argumenty bodů POP funkce v zásobníku.|  
|Konvence pro vzhled názvu|Název je předponou podtržítko (_). Následuje název znaku zavináče (@) následovaný počtem bajtů (decimální): v seznamu argumentů. Proto funkce deklarován jako `int func( int a, double b )` opatřen následujícím způsobem:`_func@12`|  
|Konvence pro posunutí|Žádné|  
  
 [/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) – možnost kompilátoru Určuje `__stdcall` pro všechny funkce, které nejsou výslovně deklarovat s jinou konvence volání.  
  
 Deklarováno s použitím funkce `__stdcall` modifikátor návratové hodnoty stejným způsobem jako funkce deklarováno s použitím [__cdecl](../cpp/cdecl.md).  
  
 Na ARM a x64 procesory, `__stdcall` je přijatá a ignoruje kompilátorem; v ARM a x64 architektury, podle konvence, jsou argumenty předány v registrech Pokud je to možné, a další argumenty se předávají v zásobníku.  
  
 U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Zadané tuto definici – třída  
  
```cpp  
struct CMyClass {  
   void __stdcall mymethod();  
};  
```  
  
 this  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 je ekvivalentní k tomuto  
  
```cpp  
void __stdcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu použití __**stdcall** výsledků ve všech `WINAPI` funkce typy zpracovanou jako standardní volání:  
  
```cpp  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)