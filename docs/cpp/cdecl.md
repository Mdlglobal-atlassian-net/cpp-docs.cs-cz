---
title: __cdecl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __cdecl_cpp
dev_langs:
- C++
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d07c34c11037132b9f9695ec889bb681c7f43951
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414490"
---
# <a name="cdecl"></a>__cdecl
**Konkrétní Microsoft**  
  
 `__cdecl` je výchozí konvence volání pro programy C a C++. Protože volající funkcí je vyčištěna zásobníku, můžete provést **vararg** funkce. `__cdecl` Konvence volání vytvoří větší spustitelných souborů než [__stdcall](../cpp/stdcall.md), protože vyžaduje každé volání funkce zahrnují kód čištění zásobníku. Následující seznam ukazuje implementaci této konvence volání.  
  
|Prvek|Implementace|  
|-------------|--------------------|  
|Pořadí předávání argumentů|Zprava doleva.|  
|Odpovědnost za údržbu zásobníku|Volání funkce vezme argumenty ze zásobníku (POP).|  
|Konvence pro vzhled názvu|Názvy, s výjimkou případů, kdy je předponou znak podtržítka (_) \__cdecl funkce, které používají C propojení jsou exportovány.|  
|Konvence pro posunutí|Neprovádí se žádné posunutí.|  
  
> [!NOTE]
>  Související informace najdete v tématu [dekorované názvy](../build/reference/decorated-names.md).  
  
 Místo `__cdecl` modifikátor před proměnnou nebo název funkce. Protože C pojmenování a konvence volání jsou výchozí, jenom musíte použít `__cdecl` v x86 kód je, když jste zadali **/gv** (vectorcall), **/Gz** (stdcall), nebo  **GR** – možnost kompilátoru (fastcall). [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) vynutí – možnost kompilátoru `__cdecl` konvence volání.  
  
 Na ARM a x64 procesory, `__cdecl` je přijato, ale obvykle ignorovat kompilátoru. Podle konvence pro procesory ARM a x64 jsou argumenty předávány v registrech vždy, když je to možné, a následné argumenty jsou předávány na zásobníku. V x64 kódu, použijte `__cdecl` přepsat **/gv** – možnost kompilátoru a použít výchozí x64 konvencí volání.  
  
 U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Při této definici třídy:  
  
```cpp  
struct CMyClass {  
   void __cdecl mymethod();  
};  
```  
  
 toto:  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 je ekvivalentem tohoto:  
  
```cpp  
void __cdecl CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je kompilátor pokyn k použití C pojmenování a konvence pro volání `system` funkce.  
  
```cpp  
// Example of the __cdecl keyword on function  
int __cdecl system(const char *);  
// Example of the __cdecl keyword on function pointer  
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)