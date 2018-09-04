---
title: Přístup k datům jazyka C++ v blocích __asm nebo C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9e4b684c878e630de81ac712fab714dc09db5ff
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685034"
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>Přístup k datům jazyka C nebo C++ v blocích __asm

**Specifické pro Microsoft**

Skvělou výhodou vloženého sestavení je možnost odkazovat na proměnné jazyka C nebo C++ podle názvu. `__asm` Bloku mohou odkazovat na žádné symboly, včetně názvy proměnných, které jsou v oboru, ve kterém se zobrazí bloku. Například pokud proměnnou C `var` je v oboru, instrukce

```cpp
__asm mov eax, var
```

uloží hodnotu `var` v EAX.

Pokud třídy, struktury nebo člen sjednocení musí mít jedinečný název `__asm` bloku může odkazovat pomocí pouze název člena, bez zadání proměnné nebo `typedef` název před období (**.**) – operátor. Pokud název členu není jedinečný, ale musíte umístit do proměnné nebo `typedef` název bezprostředně před operátor období. Například typy struktur v této sdílené složce ukázka `same_name` jako jména členů:.

Při deklarování proměnné s typy

```cpp
struct first_type hal;
struct second_type oat;
```

všechny odkazy na člen `same_name` musíte použít název proměnné, protože `same_name` není jedinečný. Ale člen `weasel` má jedinečný název, takže můžete odkazovat pomocí pouze jeho název člena:

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

Všimněte si, že vynechání název proměnné je pouze pro potřebu psaní kódu. Stejné pokyny k sestavení jsou generovány, zda je název proměnné je k dispozici.

Můžete přistupovat datové členy v jazyce C++ bez ohledu na omezení přístupu. Nelze však volat členské funkce.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>