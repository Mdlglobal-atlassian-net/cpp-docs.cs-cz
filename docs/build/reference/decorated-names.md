---
title: "Dekorované názvy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2ad7fc8e6d9b7fa261d7811086ef02738c77e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="decorated-names"></a>Dekorované názvy
Funkce, dat a objektů v programy C a C++ jsou reprezentované interně pomocí jejich dekorované názvy. A *dekorované název* je zakódovaný řetězec vytvořený kompilátor při kompilaci objektu, dat nebo definici funkce. Zaznamenává konvence volání, typy, parametry funkce a další informace společně s názvem. Tato úprava názvu, také známé jako *úprava názvu*, pomáhá linkeru najít správné funkce a objekty při propojování spustitelný soubor.  
  
 Dekorované zásady vytváření názvů změnily v různých verzí aplikace Visual C++ a mohou být různé také na různé cílové architektury. Propojte správně se zdrojové soubory, které jsou vytvořené pomocí Visual C++, C a C++ – knihovny DLL a knihovny se má kompilovat pomocí stejné sady nástrojů kompilátoru, příznaky a cílové architektury.  
  
 **Obsah**  
  
-   [Pomocí dekorované názvy](#Using)  
  
-   [Dekorované název formátu jazyka C++](#Format)  
  
-   [Dekorované název formátu a C](#FormatC)  
  
-   [Zobrazení dekorované názvy](#Viewing)  
  
-   [Názvy bez upraveného zobrazení](#Undecorated)  
  
##  <a name="Using"></a>Pomocí dekorované názvy  
 Za normálních okolností nemáte úspěšně vědět upravený název napsat kód, který se zkompiluje a odkazy. Dekorované názvy jsou interní kompilátoru a linkeru podrobností implementace. Nástroje může zpracovávat obvykle s názvem v jeho upraveného formuláře. Ale upravený název je to někdy nezbytné při zadávání názvu funkce linkeru a jiných nástrojů. Například tak, aby odpovídaly přetížených funkcí jazyka C++, členové obory názvů, třídy konstruktory, destruktory a speciální členské funkce, musíte zadat upravený název. Podrobnosti o možnost příznaky a jiné situace, které vyžadují dekorované názvy, najdete v dokumentaci nástroje a možnosti, které používáte.  
  
 Pokud změníte název funkce, třídu, konvence volání, návratový typ nebo libovolný parametr, změní se také upravený název. V takovém případě musíte získat nový upravený název a použít všude, kde je zadán upravený název.  
  
 Dekorování názvů je také důležité při propojení s kód napsaný v jiných programovacích jazyků nebo pomocí jiné kompilátory. Různé kompilátory pomocí konvence decoration jiný název. Pokud vaše spustitelný soubor odkazuje na kód napsaný v jiném jazyce, musí dát zvláštní pozor tak, aby odpovídaly importované a exportované názvy a konvence volání. Kód jazyka sestavení musí používat Visual C++ dekorované názvy a konvence volání propojení ke zdrojovému kódu, které jsou napsané v jazyce Visual C++.  
  
##  <a name="Format"></a>Dekorované název formátu jazyka C++  
 Upravený název pro funkci C++ obsahuje následující informace:  
  
-   Název funkce.  
  
-   Třída, že funkce je členem skupiny, pokud je členské funkce. To může zahrnovat třídu, která obklopuje třídu, která obsahuje funkce a tak dále.  
  
-   Obor názvů funkce patří, pokud je součástí oboru názvů.  
  
-   Typy parametrů funkce.  
  
-   Konvence volání.  
  
-   Návratový typ funkce.  
  
 Název funkce a třída zakódovaným v upravený název. Zbytek upravený název je kód, který má vnitřní význam pouze pro kompilátoru a linkeru. Následují příklady upraveného a dekorované názvy v jazyce C++.  
  
|Bez upraveného název|Upravený název|  
|----------------------|--------------------|  
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|  
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|  
  
##  <a name="FormatC"></a>Dekorované název formátu a C  
 Formulář dekorace pro funkce C závisí na konvence volání použít v jeho deklaraci, jak je znázorněno v následující tabulce. Toto je také decoration formátu, který se používá při C++ – kód je deklarovaná tak, aby měl `extern "C"` propojení. Konvence volání výchozí hodnota je `__cdecl`. Všimněte si, že v 64bitovém prostředí, nejsou dekorované funkce.  
  
|Konvence volání|Dekorace|  
|------------------------|----------------|  
|`__cdecl`|Úvodní podtržítko (**_**)|  
|`__stdcall`|Úvodní podtržítko (**_**) a na konci znaku zavináče (@) a počet bajtů v seznamu parametrů v desítkové soustavě|  
|`__fastcall`|Úvodní a koncové znak (@) a desetinné číslo představující počet bajtů v seznamu parametrů|  
|`__vectorcall`|Dva koncové znak @@ a desetinné číslo bajtů v seznamu parametrů|  
  
##  <a name="Viewing"></a>Zobrazení dekorované názvy  
 Dekorované formu názvu symbolu vám po kompilaci zdrojového souboru, který obsahuje data, objekt, nebo definice funkce nebo prototypu. K prozkoumání dekorované názvy v programu, můžete použít jednu z následujících metod:  
  
-   #### <a name="to-use-a-listing-to-view-decorated-names"></a>Použití v seznamu k zobrazení dekorované názvy  
  
    1.  Kompilování zdrojový soubor, který obsahuje data, objekt, nebo definice funkce nebo prototypu s vygenerujte v seznamu [výpis typu souboru](../../build/reference/fa-fa-listing-file.md) nastavena na sestavení s zdrojový kód – možnost kompilátoru (**/FAs**).  
  
         Zadejte například `cl /c /FAs example.cpp` na příkazovém řádku vývojáře generovat soubor seznamu example.asm.  
  
    2.  Ve výsledném souboru výpis najdete řádek, který začíná veřejné a končí středník a bez upraveného název data nebo funkce. Symbol mezi VEŘEJNÝMI a středník je upravený název.  
  
-   #### <a name="to-use-dumpbin-to-view-decorated-names"></a>Použití nástroje DUMPBIN k zobrazení dekorované názvy  
  
    1.  Chcete-li zobrazit exportovaný symboly v souboru .obj nebo .lib, zadejte `dumpbin /symbols` `objfile` na příkazovém řádku vývojáře.  
  
    2.  Dekorované formu symbol hledejte pro název bez upraveného v závorkách. Upravený název je na stejném řádku svislicí (&#124;) po znak a před upraveného název.  
  
##  <a name="Undecorated"></a>Názvy bez upraveného zobrazení  
 Undname.exe můžete převést na jeho upraveného formuláře upravený název. Tento příklad ukazuje, jak to funguje:  
  
```  
C:\>undname ?func1@a@@AAEXH@Z  
Microsoft (R) C++ Name Undecorator  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
Undecoration of :- "?func1@a@@AAEXH@Z"  
is :- "private: void __thiscall a::func1(int)"  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)   
 [Používání příkazu extern pro specifikaci propojení](../../cpp/using-extern-to-specify-linkage.md)