---
title: __fastcall | Dokumentace Microsoftu
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
ms.openlocfilehash: f50239d42c164e2f9c6876e26389eb60e710ed34
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940092"
---
# <a name="fastcall"></a>__fastcall
**Specifické pro Microsoft**  
  
 **__Fastcall** konvence volání Určuje, že argumenty funkcí mají být předány v registrech, pokud je to možné. Tato konvence volání se vztahuje pouze x86 architektury. Následující seznam ukazuje implementaci této konvence volání.  
  
|Prvek|Implementace|  
|-------------|--------------------|  
|Pořadí předávání argumentů|První dvě DWORD nebo menší argumenty, které se nacházejí v seznamu argumentů zleva doprava jsou předány v registrech ECX a EDX; všechny argumenty jsou předány v zásobníku zprava doleva.|  
|Odpovědnost za údržbu zásobníku|Volaná funkce vezme argumenty ze zásobníku.|  
|Konvence pro vzhled názvu|Zavináč (\@) je předponou názvů; zavináče následovaný počtem bajtů (v desítkové soustavě) v parametru seznam je přidán k názvům.|  
|Konvence pro posunutí|Neprovádí se žádné posunutí.|  
  
> [!NOTE]
>  Budoucí verze kompilátoru mohou používat různé registry k uložení parametrů.  
  
 Použití [GR](../build/reference/gd-gr-gv-gz-calling-convention.md) – možnost kompilátoru způsobí, že každá funkce v modulu je kompilována jako **__fastcall** Pokud není funkce deklarována s konfliktním atributem použitím nebo název funkce `main` .  
  
 **__Fastcall** – klíčové slovo je přijato a ignorováno kompilátory, které se zaměřují ARM a x64 architektury; x x64 čip, podle úmluvy první čtyři argumenty předány v registrech, pokud je to možné a další argumenty jsou předány v zásobníku. Další informace najdete v tématu [přehled x64 konvence volání](../build/overview-of-x64-calling-conventions.md). Čipu ARM až čtyři celočíselné argumenty a osm argumentů s plovoucí desetinnou čárkou mohou být předány v registrech a další argumenty jsou předány v zásobníku.  
  
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
 V následujícím příkladu se funkce `DeleteAggrWrapper` předány argumenty v registrech:  
  
```cpp  
// Example of the __fastcall keyword  
#define FASTCALL    __fastcall  
  
void FASTCALL DeleteAggrWrapper(void* pWrapper);  
// Example of the __ fastcall keyword on function pointer  
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)
