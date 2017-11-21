---
title: Inicializace CRT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1cdc3bd0d6370848859b16ce30eff6a224d83a60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crt-initialization"></a>Inicializace CRT
Toto téma popisuje, jak CRT inicializuje globální stavy v nativním kódu.  
  
 Ve výchozím nastavení zahrnuje linkeru knihovny CRT, která poskytuje vlastní kód pro spuštění. Tento kód pro spuštění inicializuje knihovny CRT, volá globální inicializátory a pak zavolá zadaný uživatelem `main` funkce pro konzolové aplikace.  
  
## <a name="initializing-a-global-object"></a>Inicializace Global – objekt  
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
  
 Podle standardu C/C++ `func()` musí být volána před provedením `main()` se spustí. Ale jej volá?  
  
 Jeden ze způsobů určení toto nastavení slouží k nastavení boru přerušení `func()`, ladit aplikaci a zkontrolujte zásobníku. To je možné, protože CRT zdrojový kód je součástí sady Visual Studio.  
  
 Při procházení funkce v zásobníku zjistíte, že je CRT ve smyčce přes seznam ukazatelů na funkce a volání každé z nich při jejich výskytu. Tyto funkce jsou buď podobná `func()` nebo konstruktory pro instance třídy.  
  
 CRT získává seznam ukazatelů na funkce z kompilátoru Visual C++. Kompilátor uvidí inicializátoru globální, vygeneruje inicializátoru dynamické v `.CRT$XCU` část (kde `CRT` je název oddílu a `XCU` je název skupiny). Získat seznam těchto dynamické inicializátory, spusťte příkaz **dumpbin nebo všechny main.obj**a poté vyhledejte `.CRT$XCU` část (když main.cpp kompilována jako soubor C++, nejedná se o soubor C). Bude podobný následujícímu:  
  
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
  
 CRT definuje dva odkazy:  
  
-   `__xc_a`v`.CRT$XCA`  
  
-   `__xc_z`v`.CRT$XCZ`  
  
 Obě skupiny nemají žádné další symboly definované s výjimkou `__xc_a` a `__xc_z`.  
  
 Teď, když linkeru čte různé `.CRT` skupin, zkombinuje je v jedné části a řadí je podle abecedy. To znamená, že uživatelská globální inicializátory (který Visual C++ compiler vloží `.CRT$XCU`) bude vždy pocházet po `.CRT$XCA` a před `.CRT$XCZ`.  
  
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
  
 Ano, knihovny CRT využívá jak `__xc_a` a `__xc_z` k určení začátku a konci seznamu globální inicializátory vzhledem ke způsobu, ve kterém se jsou nastíněny v paměti po načtení bitovou kopii.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)