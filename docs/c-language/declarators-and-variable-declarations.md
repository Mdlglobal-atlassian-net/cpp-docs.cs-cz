---
title: Deklarátor a deklarace proměnné | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a5ec2cf7984940421726dd0197dff4cf6d5ea0c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200356"
---
# <a name="declarators-and-variable-declarations"></a>Deklarátor a deklarace proměnné
Zbytek tohoto oddílu popisuje formulář opravdu zavřít a význam deklarace pro tyto typy proměnných uvedené v tomto seznamu. Konkrétně se zbývající části vysvětlují, jak deklarovat následující:  
  
|Typ proměnné|Popis|  
|----------------------|-----------------|  
|[Jednoduché proměnné](../c-language/simple-variable-declarations.md)|Jednou hodnotou proměnné typu s plovoucí desetinnou čárkou nebo celočíselné|  
|[Pole](../c-language/array-declarations.md)|Proměnné se skládá z kolekce elementů se stejným typem|  
|[Ukazatele](../c-language/pointer-declarations.md)|Proměnné, které bod na jiné proměnné a proměnné umístění (ve formě adresy) místo hodnoty obsahují|  
|[Výčet proměnné](../c-language/c-enumeration-declarations.md)|Jednoduché proměnné s integral zadejte tuto hodnotu uchování jeden z sadou pojmenovaných celočíselných konstant|  
|[Struktury](../c-language/structure-declarations.md)|Proměnné se skládá z kolekce hodnot, které mohou mít různé typy|  
|[Sjednocení](../c-language/union-declarations.md)|Proměnné se skládá z několika hodnot různých typů, které zabírají stejné prostoru úložiště|  
  
 Deklarátor je součástí deklarace, která určuje název, který má být zavedena do programu. Modifikátory může obsahovat například <strong>\*</strong> (ukazatel-do) a klíčových slov Microsoft konvence volání.  
  
 **Specifické pro Microsoft**  
  
 V deklarátoru  
  
```  
__declspec(thread) char *var;  
```  
  
 `char` je specifikátor typu `__declspec(thread)` a `*` jsou modifikátory, a `var` je název identifikátoru.  
  
 **Specifické pro END Microsoft**  
  
 Chcete-li deklarovat pole hodnot, ukazatele na hodnoty a funkce, která vrátí hodnotu zadaného typu použijete deklarátory. Deklarátory se vyskytují v deklaracích pole a ukazatel je popsáno dále v této části.  
  
## <a name="syntax"></a>Syntaxe  
 *deklarátor*:  
 &nbsp;&nbsp;*ukazatel*<sub>optimalizované</sub> *direct-declarator*  
  
 *přímé declarator*:  
 &nbsp;&nbsp;*identifikátor*  
 &nbsp;&nbsp;**(***deklarátor***)**   
 &nbsp;&nbsp;*přímé declarator***[***konstantní výraz*<sub>optimalizované</sub> **]**   
 &nbsp;&nbsp;*přímé declarator***(***seznam parametrů typu***)**   
 &nbsp;&nbsp;*přímé declarator***(***seznam identifikátorů*<sub>optimalizované</sub> **)**   
  
 *ukazatel*:  
 &nbsp;&nbsp;<strong>\*</strong> *seznam typů kvalifikátor*<sub>optimalizované</sub>  
 &nbsp;&nbsp;<strong>\*</strong> *seznam typů kvalifikátor*<sub>optimalizované</sub> *ukazatele*  
  
 *seznam typů kvalifikátor*:  
 &nbsp;&nbsp;*Kvalifikátor typu*  
 &nbsp;&nbsp;*Kvalifikátor typu seznam kvalifikátorů typu*  
  
> [!NOTE]
>  Další informace o syntaxi *deklarace* v [přehled prohlášení](../c-language/overview-of-declarations.md) nebo [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md) pro syntaxi, která odkazuje na *deklarátor*.  
  
 Když deklarátorem sestává z identifikátoru bez úprav, položka deklarované má základního typu. Pokud hvězdičku (<strong>\*</strong>) se zobrazí nalevo od identifikátoru, je změněn na typ na typ ukazatele. Pokud je identifikátor následovaný hranatými závorkami (**[ ]**), typ je upravit tak, aby typ pole. Pokud identifikátor je následována závorky, je změněn na typ na typ funkce. Další informace o interpretaci prioritu uvnitř deklarací najdete v tématu [interpretace složitějších Deklarátorů](../c-language/interpreting-more-complex-declarators.md).  
  
 Každý deklarátor deklaruje aspoň jeden identifikátor. Deklarátor musí obsahovat specifikátor typu pro jít o úplnou deklaraci. Specifikátor typu poskytuje typ prvků typu pole, typ objektu odkazovaného typu ukazatele nebo návratového typu funkce.  
  
 [Pole](../c-language/array-declarations.md) a [ukazatel](../c-language/pointer-declarations.md) deklarace jsou popsány podrobněji dále v tomto oddílu. Následující příklady znázorňují pár jednoduchých formy deklarátory:  
  
```  
int list[20]; // Declares an array of 20 int values named list  
char *cp;     // Declares a pointer to a char value  
double func( void ); // Declares a function named func, with no   
                     // arguments, that returns a double value  
int *aptr[10] // Declares an array of 10 pointers  
```  
  
 **Specifické pro Microsoft**  
  
 Kompilátor Microsoft C neomezuje počet deklarátory, které můžete upravit aritmetický, struktura nebo typu sjednocení. Počet je omezen pouze dostupnou paměť.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)