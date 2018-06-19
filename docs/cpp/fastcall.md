---
title: __fastcall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fastcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03f286f21f213f5b2a193ccb824ba22b7c7c1f00
ms.sourcegitcommit: 39585672df8874fb5df4e70de97cd7f328fe9880
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2018
ms.locfileid: "34153116"
---
# <a name="fastcall"></a>__fastcall
**Konkrétní Microsoft**  
  
 `__fastcall` Konvence volání Určuje, že argumenty funkce mají být předány v registrech, pokud je to možné. Tato konvence volání se vztahuje pouze x86 architektura. Následující seznam ukazuje implementaci této konvence volání.  
  
|Prvek|Implementace|  
|-------------|--------------------|  
|Pořadí předávání argumentů|První dva DWORD nebo menší argumenty, které se nacházejí v seznamu argumentů zleva doprava se předávají v ECX a EDX registry; všechny další argumenty se předávají v zásobníku zprava doleva.|  
|Odpovědnost za údržbu zásobníku|Volá argumenty bodů POP funkce v zásobníku.|  
|Konvence pro vzhled názvu|Znaku zavináče (\@) předponou názvy; je seznamu je znak následovaný počtem bajtů (decimální) v parametru na konci na názvy.|  
|Konvence pro posunutí|Neprovádí se žádné posunutí.|  
  
> [!NOTE]
>  Budoucí kompilátoru verze může pomocí různých registry uložit parametry.  
  
 Pomocí [GR](../build/reference/gd-gr-gv-gz-calling-convention.md) – možnost kompilátoru způsobí, že jednotlivé funkce v modulu zkompilovat jako `__fastcall` Pokud je funkce deklarována s použitím konfliktní atribut, nebo je název funkce `main`.  
  
 `__fastcall` – Klíčové slovo je přijatá a ignorovat kompilátory, které se zaměřují ARM a x64 architektury; na x64 čip dle konvencí se první čtyři argumenty se předávají v registrech, pokud je to možné a další argumenty se předávají v zásobníku. Další informace najdete v tématu [přehled x64 konvence volání](../build/overview-of-x64-calling-conventions.md). Až čtyři celé číslo na čip TPM ARM, argumentů a osmi argumenty s plovoucí desetinnou čárkou mohou být předány v registrech a další argumenty se předávají v zásobníku.  
  
 U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Při této definici třídy:  
  
```cpp  
struct CMyClass {  
   void __fastcall mymethod();  
};  
```  
  
 toto:  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 je ekvivalentem tohoto:  
  
```cpp  
void __fastcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, funkce `DeleteAggrWrapper` je předaná registry argumenty:  
  
```cpp  
// Example of the __fastcall keyword  
#define FASTCALL    __fastcall  
  
void FASTCALL DeleteAggrWrapper(void* pWrapper);  
// Example of the __ fastcall keyword on function pointer  
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)
