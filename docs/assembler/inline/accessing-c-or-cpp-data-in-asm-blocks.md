---
title: Přístup k datům jazyka C nebo C++ v blocích __asm
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: b4341f87226118906749dcdb18b9227e68be6a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318082"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>Přístup k datům jazyka C nebo C++ v blocích __asm

**Specifické pro Microsoft**

Velké pohodlí vřádkové sestavení je schopnost odkazovat na c nebo C++ proměnné podle názvu. Blok `__asm` může odkazovat na všechny symboly, včetně názvů proměnných, které jsou v oboru, kde se zobrazí blok. Například, pokud c `var` proměnná je v oboru, instrukce

```cpp
__asm mov eax, var
```

ukládá hodnotu `var` v EAX.

Pokud má člen třídy, struktury nebo sjednocení `__asm` jedinečný název, může na něj blok odkazovat `typedef` pouze pomocí názvu člena, aniž by byl před operátorem period (**.**) specifikován proměnná nebo název. Pokud však název člena není jedinečný, musíte `typedef` umístit proměnnou nebo název bezprostředně před operátor období. Například typy struktury v následujícím `same_name` vzorku sdílejí jako název svého člena:.

Pokud deklarujete proměnné s typy

```cpp
struct first_type hal;
struct second_type oat;
```

všechny odkazy na `same_name` člen musí použít `same_name` název proměnné, protože není jedinečný. Ale člen `weasel` má jedinečný název, takže na něj můžete odkazovat pouze pomocí jeho názvu člena:

```cpp
// InlineAssembler_Accessing_C_asm_Blocks.cpp
// processor: x86
#include <stdio.h>
struct first_type
{
   char *weasel;
   int same_name;
};

struct second_type
{
   int wonton;
   long same_name;
};

int main()
{
   struct first_type hal;
   struct second_type oat;

   __asm
   {
      lea ebx, hal
      mov ecx, [ebx]hal.same_name ; Must use 'hal'
      mov esi, [ebx].weasel       ; Can omit 'hal'
   }
   return 0;
}
```

Všimněte si, že vynechání názvu proměnné je pouze pohodlí kódování. Stejné pokyny sestavení jsou generovány bez ohledu na to, zda je k dispozici název proměnné.

Můžete přistupovat k datovým členům v jazyce C++ bez ohledu na omezení přístupu. Však nelze volat členské funkce.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
