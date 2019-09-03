---
title: init_seg – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 5e57ea0eedfc1df6e196391c5edd3acfbad0a7c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221001"
---
# <a name="init_seg-pragma"></a>init_seg – direktiva pragma

**C++Konkrétní**

Určuje klíčové slovo nebo oddíl kódu, který má vliv na pořadí, ve kterém je spuštěn spouštěcí kód.

## <a name="syntax"></a>Syntaxe

> **#pragma init_seg (** { **Compiler** | **lib** | **User** | "*název oddílu*" [ **,** *Func-Name* ]} **)**

## <a name="remarks"></a>Poznámky

Pojem *segment* a *oddíl* má stejný význam jako v tomto článku.

Vzhledem k tomu, že kód je někdy vyžadován k inicializaci globálních statických objektů, je nutné určit, kdy vytvořit objekty. Konkrétně je důležité použít direktivu pragma **init_seg** v knihovnách DLL (Dynamic-Link Library) nebo v knihovnách, které vyžadují inicializaci.

Možnosti direktivy pragma **init_seg** jsou:

**přepínač**\
Vyhrazeno pro inicializaci knihovny runtime jazyka C společnosti Microsoft. Objekty v této skupině jsou konstruovány jako první.

**Knihovna**\
K dispozici pro inicializace výrobců tříd třetích stran. Objekty v této skupině jsou konstruovány po označení jako **kompilátor**, ale před všemi ostatními.

**uživatelský**\
K dispozici pro libovolného uživatele. Objekty v této skupině jsou vytvářeny jako poslední.

*název oddílu*\
Umožňuje explicitní určení oddílu inicializace. Objekty v uživatelsky definovaném *oddílu – název* nejsou implicitně sestaveny. Jejich adresy se ale nacházejí v části s názvem podle *názvu oddílu*.

*Název oddílu* , který udělíte, bude obsahovat odkazy na pomocné funkce, které vytvoří globální objekty deklarované po direktivě pragma v tomto modulu.

Seznam názvů, které byste neměli používat při vytváření oddílu, najdete v tématu [/Section](../build/reference/section-specify-section-attributes.md).

*Func-Name*\
Určuje funkci, která bude volána místo `atexit` při ukončení programu. Tato pomocná funkce také volá [atexit](../c-runtime-library/reference/atexit.md) s ukazatelem na destruktor pro globální objekt. Pokud zadáte identifikátor funkce v direktivě pragma formuláře,

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

pak bude funkce volána místo knihovny `atexit`run-time jazyka C. Umožňuje vytvořit seznam destruktorů, které mají být volány, až budete připraveni na zničení objektů.

Pokud potřebujete odložit inicializaci (například v knihovně DLL), můžete se rozhodnout zadat název oddílu explicitně. Váš kód musí následně volat konstruktory pro každý statický objekt.

Neexistují žádné uvozovky kolem identifikátoru pro `atexit` nahrazení.

Vaše objekty budou stále umístěny v oddílech definovaných jinými `XXX_seg` direktivami pragma.

Objekty, které jsou deklarovány v modulu, nejsou automaticky inicializovány modulem runtime jazyka C. Váš kód musí provést inicializaci.

Ve výchozím nastavení `init_seg` jsou oddíly jen pro čtení. Pokud je `.CRT`název oddílu, kompilátor tiše změní atribut jen pro čtení, a to i v případě, že je označený jako Read a Write.

V jednotce překladu nemůžete zadat **init_seg** více než jednou.

I v případě, že váš objekt nemá uživatelem definovaný konstruktor, který je explicitně definován v kódu, kompilátor může vygenerovat jeden za vás. Například může vytvořit jednu pro svázání ukazatelů v tabulce. V případě potřeby váš kód volá konstruktor generovaný kompilátorem.

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

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
