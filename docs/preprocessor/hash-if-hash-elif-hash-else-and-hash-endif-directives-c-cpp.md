---
title: '#Pokud, #elif, #else a #endif (C/C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
dev_langs:
- C++
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9d4f941298159b8a3ea1aa3fe37efd1e6dc68ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="if-elif-else-and-endif-directives-cc"></a>Direktivy #if, #elif, #else a #endif (C/C++)
`#if` Direktivy s `#elif`, `#else`, a `#endif` direktivy, ovládací prvky kompilaci části zdrojového souboru. Pokud píšete výraz (po `#if`) má nenulovou hodnotu, skupině řádek hned za `#if` – direktiva se uchovávají v jednotce překlad.  
  
## <a name="grammar"></a>Gramatika  
 *Podmíněné* :  
 *Pokud část elif částí*vyjádřit výslovný*část else*opt*endif řádku*  
  
 *Pokud součást* :  
 *Pokud řádek textu*  
  
 *Pokud line* :  
 **#if***konstantní výraz*  
  
 **#ifdef***identifikátor*  
  
 **#ifndef***identifikátor*  
  
 *elif – částí* :  
 *elif – řádek textu*  
  
 *elif – částí elif – řádek textu*  
  
 *elif-line* :  
 **#elif***konstantní výraz*  
  
 *část else* :  
 *jiný řádek textu*  
  
 *else řádku* :  
 `#else`  
  
 *endif-line* :  
 `#endif`  
  
 Každý `#if` – direktiva v zdrojový soubor musí odpovídat podle uzavírající `#endif` – direktiva. Libovolný počet `#elif` direktivy může vyskytovat mezi `#if` a `#endif` direktivy, ale maximálně jeden `#else` – direktiva je povolen. `#else` – Direktiva, pokud existuje, musí být poslední – direktiva před `#endif`.  
  
 `#if`, `#elif`, `#else`, A `#endif` direktivy lze vnořit v části textu jiné `#if` direktivy. Všechny vnořené `#else`, `#elif`, nebo `#endif` – direktiva patří do nejbližší předchozí `#if` – direktiva.  
  
 Všechny podmíněné kompilace direktivy, jako například `#if` a **#ifdef**, musí odpovídat s ukončovací `#endif` direktivy před konec souboru, jinak se generuje chybovou zprávu. Když podmíněné kompilace direktivy jsou obsaženy v zahrnout soubory, musí vyhovovat stejných podmínek: musí být žádné neodpovídající direktivy podmíněné kompilace na konci souboru zahrnout.  
  
 Nahrazení makra je provést v rámci součást příkazového řádku, který následuje `#elif` příkazů, tak mohou být používány makro volání *konstantní výraz*.  
  
 Preprocesor vybere jeden z daného výskyty *text* pro další zpracování. Blok zadaný v *text* může být jakékoli pořadí textu. Můžete ho zabírají více než jeden řádek. Obvykle *text* je program text, který má význam pro kompilátor nebo preprocesor.  
  
 Preprocesor procesů vybrané *text* a předává je kompilátoru. Pokud *text* obsahuje preprocesor – direktivy preprocesoru neprovede tyto direktivy. Pouze text bloky vybraná preprocesor kompilovány.  
  
 Preprocesor vybere jeden *text* položky vyhodnocením konstantní výraz, který následuje každý `#if` nebo `#elif` – direktiva, dokud nenajde true (nenulové) konstantní výraz. Vybere veškerý text (včetně jiných preprocesor – direktivy počínaje **#**) až přidružené `#elif`, `#else`, nebo `#endif`.  
  
 Pokud všechny výskyty *konstantní výraz* jsou nastavena hodnota false, nebo pokud žádné `#elif` direktivy nezobrazí, preprocesor vybere bloku textu po `#else` klauzule. Pokud `#else` je vynechaná klauzule a všechny instance *konstantní výraz* v `#if` bloku jsou false, je vybrán žádný text blok.  
  
 *Konstantní výraz* je konstantní výraz celého čísla. tyto další omezení:  
  
-   Výrazy musí mít celočíselný typ a může obsahovat jenom konstanty typu integer, konstanty znaků a **definované** operátor.  
  
-   Nelze použít ve výrazu `sizeof` nebo operátor přetypování.  
  
-   Cílové prostředí nemusí být možné představují všechny rozsahy celých čísel.  
  
-   Překlad představuje typ `int` stejný jako typ **dlouho**, a `unsigned int` stejný jako `unsigned long`.  
  
-   Překladač může překládat konstanty znaků na sadu hodnoty kódu liší od sady pro cílové prostředí. K určení vlastností, cílové prostředí, zkontrolujte hodnoty makra z omezení. H v aplikaci sestavené pro cílové prostředí.  
  
-   Výraz nesmí provádět žádné prostředí dotazy a musí zůstat izolované od podrobnosti implementace v cílovém počítači.  

## <a name="defined"></a>definováno  
 Operátor preprocesoru **definované** mohou být používány speciální konstantní výrazy, jak ukazují následující syntaxi:  
  
 definované ( `identifier` )  
  
 Definované `identifier`  
  
 Tento konstantní výraz se považuje za hodnotu true (nenulové hodnoty), pokud *identifikátor* je aktuálně definován; jinak, je podmínka vyhodnocena jako false (0). Identifikátor definován jako prázdný textový se považuje za definované. **Definované** – direktiva mohou být používány `#if` a `#elif` – direktiva, ale nikde jinde.  
  
 V následujícím příkladu `#if` a `#endif` direktivy řízení kompilace jednoho ze tří volání funkce:  
  
```  
#if defined(CREDIT)  
    credit();  
#elif defined(DEBIT)  
    debit();  
#else  
    printerror();  
#endif  
```  
  
 Volání funkce `credit` je kompilovat, pokud identifikátor `CREDIT` je definována. Pokud identifikátor `DEBIT` definované, volání funkce `debit` kompiluje. Pokud je definována ani identifikátor, volání `printerror` kompiluje. Všimněte si, že `CREDIT` a `credit` jsou jedinečné identifikátory jazyka C a C++, protože jejich případech se liší.  
  
 Podmíněná kompilace příkazy v následujícím příkladu se předpokládá dříve definované konstantě symbolický s názvem `DLEVEL`.  
  
```  
#if DLEVEL > 5  
    #define SIGNAL  1  
    #if STACKUSE == 1  
        #define STACK   200  
    #else  
        #define STACK   100  
    #endif  
#else  
    #define SIGNAL  0  
    #if STACKUSE == 1  
        #define STACK   100  
    #else  
        #define STACK   50  
    #endif  
#endif  
#if DLEVEL == 0  
    #define STACK 0  
#elif DLEVEL == 1  
    #define STACK 100  
#elif DLEVEL > 5  
    display( debugptr );  
#else  
    #define STACK 200  
#endif  
```  
  
 První `#if` bloku ukazuje dvě sady vnořené `#if`, `#else`, a `#endif` direktivy. První sadu direktivy zpracování pouze v případě `DLEVEL > 5` hodnotu true. V opačném příkazy za #**else** se zpracovávají.  
  
 `#elif` a `#else` direktivy v druhém příkladu se používají k si ho čtyři voleb, na základě hodnoty z `DLEVEL`. Konstanta `STACK` je nastaven na hodnotu 0, 100, 200, v závislosti na definici `DLEVEL`. Pokud `DLEVEL` je větší než 5 a potom příkaz  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 Kompiluje a `STACK` není definován.  
  
 Běžně používá pro Podmíněná kompilace je zabránit více zahrnutí stejný soubor hlaviček. V jazyce C++, kde třídy jsou často definovány v soubory hlaviček, konstrukce takto lze zabránit několik definic:  
  
```  
/*  EXAMPLE.H - Example header file  */  
#if !defined( EXAMPLE_H )  
#define EXAMPLE_H  
  
class Example  
{  
...  
};  
  
#endif // !defined( EXAMPLE_H )  
```  
  
 Předchozí kód zkontroluje, zda symbolický konstanta `EXAMPLE_H` je definována. Pokud ano, soubor je již součástí a nemusí být znovu zpracována. Pokud ne, konstanta `EXAMPLE_H` je definována označit příklad. H jako již zpracována.  

## <a name="hasinclude"></a>__has_include
**Visual Studio 2017 verze 15.3 a novější**: Určuje, zda je k dispozici pro zahrnutí hlavičku knihovny:  

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)