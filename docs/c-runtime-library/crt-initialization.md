---
title: Inicializace CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 965955cf5c92ba627227292d513c9b2bda57cd48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031914"
---
# <a name="crt-initialization"></a>Inicializace CRT

Toto téma popisuje, jak CRT inicializuje globální státy v nativním kódu.

Ve výchozím nastavení linker zahrnuje knihovny CRT, které poskytuje vlastní spouštěcí kód. Tento kód při spuštění inicializuje knihovny CRT, volá globálních inicializátorů a pak zavolá, pokud uživatel `main` funkce pro konzolové aplikace.

## <a name="initializing-a-global-object"></a>Inicializace globálního objektu

Vezměte v úvahu následující kód:

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

Podle standardu jazyka C/C++ `func()` musí být volána před `main()` provádí. Ale který volá?

Jeden ze způsobů, jak zjistit, je nastavit zarážku `func()`ladit aplikaci a zkontrolujte zásobníku. To je možné, protože zdrojový kód CRT je součástí sady Visual Studio.

Při procházení funkcí v zásobníku, zjistíte, že je opakování ve smyčce přes seznam ukazatelů na funkce a volání každé z nich je narazí CRT. Tyto funkce jsou podobné `func()` nebo konstruktory pro instance třídy.

Seznam ukazatelů na funkce CRT získá z kompilátoru jazyka Visual C++. Když kompilátor narazí globální inicializační výraz, vygeneruje dynamického inicializátoru v `.CRT$XCU` oddílu (ve kterém `CRT` je název oddílu, který a `XCU` je název skupiny). Získat seznam těchto dynamických inicializátorů. Spusťte příkaz **dumpbin/all main.obj**a potom je prohledejte `.CRT$XCU` části (Pokud main.cpp je zkompilován jako soubor jazyka C++, nejedná se o soubor jazyka C). Je podobný následujícímu:

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                                Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  ------
00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT definuje dva ukazatele:

- `__xc_a` V `.CRT$XCA`

- `__xc_z` V `.CRT$XCZ`

Obě skupiny nemají žádné jiné symboly definované s výjimkou `__xc_a` a `__xc_z`.

Teď, když linker přečte různé `.CRT` skupin, zkombinuje je v jednom oddílu a řadí je podle abecedy. To znamená, že uživatelský globálních inicializátorů (které kompilátor Visual C++ umístí `.CRT$XCU`) budou přicházet vždy po `.CRT$XCA` a před `.CRT$XCZ`.

V části bude vypadat takto:

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Proto Knihovna CRT používá `__xc_a` a `__xc_z` určit začátku a konce seznamu globálních inicializátorů vzhledem ke způsobu, ve kterém jsou jsou nastíněny v paměti po načtení obrázku.

## <a name="see-also"></a>Viz také

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)