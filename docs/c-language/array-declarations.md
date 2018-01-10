---
title: Deklarace pole | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06742239c48503a5917317a674a39f50a38702c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="array-declarations"></a>Deklarace pole
"Array deklarace" názvy pole a určuje typ jejích elementů. Můžete také definovat počet prvků v poli. Proměnná s typ pole je považován za ukazatel na typ prvků pole.  
  
## <a name="syntax"></a>Syntaxe  
 `declaration`:  
 *specifikátory deklarace init deklarátor list* opt**;**  
  
 *Init – deklarátor seznamu*:  
 *Init – deklarátor*  
  
 *Init – deklarátor seznamu* **,***init deklarátor*   
  
 *Init – deklarátor*:  
 *deklarátor*  
  
 *deklarátor***=***inicializátoru*   
  
 `declarator`:  
 *ukazatel* opt*přímo deklarátor*  
  
 *deklarátor přímo*:  
 *deklarátor přímo***[***konstantní výraz* opt**]**   
  
 Protože *konstantní výraz* je volitelná, syntaxe má dva způsoby:  
  
-   První formulář definuje proměnná typu pole. *Konstantní výraz* argument v hranatých závorkách určuje počet prvků v poli. *Konstantní výraz*, pokud existuje, musí mít celočíselný typ a hodnotu větší než nula. Každý prvek má typ poskytují *specifikátor typu*, které mohou být jakéhokoli typu, s výjimkou `void`. K elementu pole nemůže být typu funkce.  
  
-   Druhý formulář deklaruje proměnné, která byla definována jinde. Se vynechá *konstantní výraz* argument v závorkách, ale není závorky. Tento formulář můžete použít pouze, pokud jste dříve inicializovat pole deklarované jako parametr, nebo je deklarován jako odkaz na pole explicitně definován jinde v programu.  
  
 V obou forms *přímo deklarátor* názvy proměnné a můžete je upravit typ proměnné. Hranaté závorky (**[]**) následující *přímo deklarátor* upravit deklarátor na typ pole.  
  
 Kvalifikátory typu se mohou objevit v deklaraci objekt typu pole, ale platí kvalifikátory elementy spíše než pole sám sebe.  
  
 Pole polí ("multidimenzionální" array) můžou deklarovat podle deklarátor pole se seznamem konstantní výrazy v závorkách v této podobě:  
  
```  
  
type-specifier  
declarator [constant-expression] [constant-expression] ...  
```  
  
 Každý *konstantní výraz* do hranatých závorek definuje počet elementů v dané dimenzi: dvourozměrná pole mají dva výrazy v závorkách, trojrozměrné pole mají tři a tak dále. První konstantní výraz můžete vynechat, pokud máte inicializovat pole deklarované jako parametr, nebo je deklarován jako odkaz na pole explicitně definován jinde v programu.  
  
 Můžete definovat pole ukazatele na různé typy objektů pomocí složité deklarátory, jak je popsáno v [interpretace více složité Deklarátory](../c-language/interpreting-more-complex-declarators.md).  
  
 Pole jsou uloženy řádek. Například následující pole se skládá z dva řádky s tři sloupce:  
  
```  
char A[2][3];  
```  
  
 Tři sloupce prvního řádku jsou uloženy nejprve, za nímž následuje tři sloupce druhého řádku. To znamená, že poslední dolní index se bude lišit nejvíce rychle.  
  
 Odkázat na jednotlivé elementu pole pomocí výraz dolního indexu, jak je popsáno v [přípony operátory](../c-language/postfix-operators.md).  
  
## <a name="examples"></a>Příklady  
 Tyto příklady ilustrují deklarace pole:  
  
```  
float matrix[10][15];  
```  
  
 Dvourozměrná pole s názvem `matrix` má 150 elementy, každý s **float** typu.  
  
```  
struct {  
    float x, y;  
} complex[100];  
```  
  
 Toto je deklaraci pole struktury. Toto pole má 100 prvků; Každý prvek je struktura obsahující dva členy.  
  
```  
extern char *name[];  
```  
  
 Tento příkaz deklaruje typ a název pole ukazatele na `char`. Skutečné definice `name` dochází jinde.  
  
 **Konkrétní Microsoft**  
  
 Typ celé číslo, které jsou požadované pro uchovávání maximální velikost pole je velikost **size_t –**. Definované v záhlaví souboru STDDEF. H, **size_t –** je `unsigned int` s rozsahem 0x00000000 k 0x7CFFFFFF.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)