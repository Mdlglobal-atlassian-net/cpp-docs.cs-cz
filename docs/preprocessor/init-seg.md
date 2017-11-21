---
title: "init_seg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc8f7c636a3d013d1dd7001e281d35af07961b6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="initseg"></a>init_seg
**Konkrétní C++**  
  
 Určuje oddíl – klíčové slovo nebo kód, který má vliv pořadí, ve které spuštění je prováděna kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )  
```  
  
## <a name="remarks"></a>Poznámky  
 Význam podmínky *segment* a *části* se zaměňovat v tomto tématu.  
  
 Protože inicializace globální statické objekty může zahrnovat provádění kódu, je nutné zadat klíčové slovo, které definuje, když jsou tyto objekty k zkonstruovat. Je zvláště důležité pro použití **init_seg –** – Direktiva pragma v dynamické knihovny (DLL) nebo knihovny, které vyžadují inicializace.  
  
 Možnosti, které se **init_seg –** – Direktiva pragma jsou:  
  
 **kompilátoru**  
 Vyhrazeno pro inicializaci běhové knihovny Microsoft C. Nejprve se vytvářejí objekty v této skupině.  
  
 **lib**  
 K dispozici pro inicializacích dodavateli třetích stran – knihovna tříd. Objekty v této skupině se vytvářejí po ty označen jako **kompilátoru** , ale před všechny ostatní.  
  
 **uživatel**  
 K dispozici pro všechny uživatele. Objekty v této skupině se vytvářejí poslední.  
  
 *Název oddílu*  
 Umožňuje explicitní specifikaci části inicializace. Objekty v zadán uživatel *název oddílu* nejsou sestavený implicitně; však jejich adresy jsou umístěny v části s názvem podle *název oddílu*.  
  
 Název oddílu, který poskytnete bude obsahovat odkazy na pomocných funkcí, které bude vytvořit globální objekty, které jsou deklarované v tomto modulu po – Direktiva pragma.  
  
 Seznam názvů byste neměli používat při vytváření oddílu najdete v tématu [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 *Název Func*  
 Určuje funkce, která se má volat místě `atexit` při ukončení programu. Tato pomocná funkce také voláním [atexit](../c-runtime-library/reference/atexit.md) pomocí ukazatele destruktoru globální objektu. Pokud zadáte v – Direktiva pragma formuláře, identifikátor – funkce  
  
```  
int __cdecl myexit (void (__cdecl *pf)(void))  
```  
  
 pak volaná funkce místo běhové knihovny jazyka C `atexit`. Můžete vytvořit seznam destruktory, které bude potřeba volat, když budete chtít destroy objekty.  
  
 Pokud potřebujete odložení inicializace (například v knihovně DLL) můžete explicitně zadat název oddílu. Konstruktory musí volat pak pro každý objekt statické.  
  
 Neexistují žádné uvozovky, do kterých identifikátor `atexit` nahrazení.  
  
 Vašich objektů bude stále umístěny v definované jiných XXX_seg pragmas částech.  
  
 Objekty, které jsou deklarované v modulu nebude automaticky iniciovány běhu C. Potřebujete udělat tento sami.  
  
 Ve výchozím nastavení `init_seg` oddíly jsou jen pro čtení. Pokud je název oddílu. CRT, kompilátor bude bezobslužně změnit atribut, který se jen pro čtení, i když je určen jen pro čtení, zápisu.  
  
 Nelze zadat **init_seg –** více než jednou v jednotce překlad.  
  
 I v případě, že vaše objekt nemá konstruktor definovaný uživatelem, konstruktor nejsou výslovně definované v kódu, kompilátor může generovat jednu (například pro vazbu ukazatele tabulky v).  Váš kód bude proto muset volat konstruktor generované kompilátorem.  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)