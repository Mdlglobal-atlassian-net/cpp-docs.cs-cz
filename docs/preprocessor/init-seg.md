---
title: init_seg – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 078026836b5f5c1fafe89e5f5e49bf0693be9250
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466299"
---
# <a name="initseg"></a>init_seg
**Specifické pro C++**  
  
Určuje část – klíčové slovo nebo kód, který má vliv pořadí spuštění po spuštění kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )  
```  
  
## <a name="remarks"></a>Poznámky  
 
Významy pojmů *segmentu* a *části* jsou v tomto tématu zaměnitelné.  
  
Inicializace globálních statických objektů může zahrnovat provádění kódu, a proto je nutné zadat klíčové slovo, který definuje, kdy jsou objekty byly konstruovány. Je zvláště důležité pro použití **init_seg –** direktivy pragma v dynamické knihovny (DLL) nebo nutnosti inicializace knihovny.  
  
Možnosti **init_seg –** – Direktiva pragma jsou:  
  
*compiler*  
Vyhrazeno pro inicializaci knihovny run-time C společnosti Microsoft. Objekty v této skupině jsou vytvořeny jako první.  
  
*lib*  
K dispozici pro třídy knihovny třetí strany dodavatelů inicializace. Objekty v této skupině jsou vytvořeny po těch označen jako *kompilátoru* , ale před všechny ostatní.  
  
*Uživatel*  
Přístupné všem uživatelům. Objekty v této skupině jsou vytvořeny jako poslední.  
  
*Název oddílu*  
Umožňuje explicitní specifikaci části inicializace. Objekty v zadané uživatelem *název oddílu* nejsou implicitně vytvořený, ale jejich adresy jsou umístěné v části s názvem podle *název oddílu*.  
  
Dáte název oddílu, který bude obsahovat ukazatele na funkce pomocné rutiny, které vytvoří globální objekty deklarované v tomto modulu za direktivou.  
  
Seznam názvů byste neměli používat při tvorbě oddílu, naleznete v tématu [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
*func-name*  
Určuje funkci, která se má volat místo `atexit` při ukončení programu. Tato pomocná funkce také voláním [atexit](../c-runtime-library/reference/atexit.md) s ukazatelem na destruktor pro globální objekt. Pokud zadáte identifikátor funkce – Direktiva pragma formuláře  
  
```  
int __cdecl myexit (void (__cdecl *pf)(void))  
```  
  
pak zavolá se funkce namísto knihovny run-time C `atexit`. To umožňuje sestavit seznam destruktory, které budou muset být volána, když budete chtít zničit objekty.  
  
Pokud potřebujete odložení inicializace (například v knihovně DLL) můžete zadat název oddílu, který explicitně. Konstruktory musíte pak zavolat pro každý statických objektů.  
  
Neexistují žádné uvozovky kolem identifikátor `atexit` nahrazení.  
  
Objekty budou stále umístěny v části určené jiných XXX_seg direktivy pragma.  
  
Objekty, které jsou deklarovány v modulu nebude automaticky inicializován pomocí C run-time. Je potřeba udělat tento sami.  
  
Ve výchozím nastavení `init_seg` oddíly jsou jen pro čtení. Pokud je název oddílu. CRT, kompilátor tiše změní atribut jen pro čtení, i když je určen pro čtení, zápis.  
  
Nelze zadat **init_seg –** více než jednou v jednotce překladu.  
  
I v případě, že váš objekt nemá žádné uživatelem definovaný konstruktor, konstruktor nejsou explicitně definovány v kódu, kompilátor může vygenerovat (například pro vazbu ukazatele v tabulce).  Váš kód bude mít tudíž volat konstruktor vygenerovaný kompilátorem.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// pragma_directive_init_seg.cpp  
#include <stdio.h>  
#pragma warning(disable : 4075)  
  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors we need to call  
PF pfx[200];    // pointers to destructors.  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() { puts("A()"); }  
   ~A() { puts("~A()"); }  
};  
  
// ctor & dtor called by CRT startup code   
// because this is before the pragma init_seg  
A aaaa;   
  
// The order here is important.  
// Section names must be 8 characters or less.  
// The sections with the same name before the $  
// are merged into one section. The order that  
// they are merged is determined by sorting  
// the characters after the $.  
// InitSegStart and InitSegEnd are used to set  
// boundaries so we can find the real functions  
// that we need to call for initialization.  
  
#pragma section(".mine$a", read)  
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;  
  
#pragma section(".mine$z",read)  
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;  
  
// The comparison for 0 is important.  
// For now, each section is 256 bytes. When they  
// are merged, they are padded with zeros. You  
// can't depend on the section being 256 bytes, but  
// you can depend on it being padded with zeros.  
  
void InitializeObjects () {  
   const PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if (*x) (*x)();  
}  
  
void DestroyObjects () {  
   while (cxpf>0) {  
      --cxpf;  
      (pfx[cxpf])();  
   }  
}  
  
// by default, goes into a read only section  
#pragma init_seg(".mine$m", myexit)  
  
A bbbb;   
A cccc;  
  
int main () {  
   InitializeObjects();  
   DestroyObjects();  
}  
```  
  
```Output  
A()  
A()  
A()  
~A()  
~A()  
~A()  
```  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)