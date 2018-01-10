---
title: "Dočasné objekty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5bb0c065158df339fb7e0a5cf39b4588411babe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="temporary-objects"></a>Dočasné objekty
V některých případech je pro kompilátor nezbytné vytvořit dočasné objekty. Tyto dočasné objekty mohou být vytvořeny z následujících důvodů:  
  
-   Inicializace odkazu `const` s inicializátorem typu odlišného od základního typu inicializovaného odkazu.  
  
-   Uložení návratové hodnoty funkce, která vrací uživatelský typ. Tyto dočasné objekty jsou vytvořeny pouze v případě, že program nekopíruje hodnotu vrácenou objektu. Příklad:  
  
    ```  
    UDT Func1();    //  Declare a function that returns a user-defined  
                    //   type.  
  
    ...  
  
    Func1();        //  Call Func1, but discard return value.  
                    //  A temporary object is created to store the return  
                    //   value.  
    ```  
  
     Protože vrácená hodnota není do jiného objektu zkopírována, je vytvořen dočasný objekt. Častější případ, kdy jsou dočasné objekty vytvořeny, je při vyhodnocení výrazu, kde musí být volány funkce přetíženého operátoru. Tyto funkce přetíženého operátoru vrátí uživatelský typ, který často není zkopírován do jiného objektu.  
  
     Vezměte v úvahu výraz `ComplexResult = Complex1 + Complex2 + Complex3`. Výraz `Complex1 + Complex2` je vyhodnocen a výsledek je uložen v dočasném objektu. Další, výraz *dočasné* `+ Complex3` je vyhodnocena a výsledek je zkopírovat do `ComplexResult` (za předpokladu, že operátor přiřazení není přetížený).  
  
-   Uložení výsledku přetypování do uživatelského typu. Když je objekt daného typu explicitně převeden na uživatelský typ, tento nový objekt je zkonstruován jako dočasný objekt.  
  
 Dočasné objekty mají dobu života, která je definována bodem jejich vytvoření a bodem, ve kterém jsou zničeny. Libovolný výraz, který vytvoří více než jeden dočasný objekt, je nakonec zničí v obráceném pořadí, než ve kterém byly vytvořeny. Body, ve kterých dochází ke zničení, jsou uvedeny v následující tabulce.  
  
### <a name="destruction-points-for-temporary-objects"></a>Body zničení dočasných objektů  
  
|Důvod vytvoření dočasného objektu|Bod zničení|  
|------------------------------|-----------------------|  
|Výsledek vyhodnocení výrazu|Všechny dočasné objekty vytvořené jako výsledek vyhodnocení výrazu jsou zničeny na konci příkazu výrazu (v místě středníku) nebo na konci řídicích výrazů příkazů `for`, `if`, `while`, `do` a `switch`.|  
|Inicializace odkazů `const`|Pokud není inicializátorem l-hodnota stejného typu jako inicializovaný odkaz, je vytvořen dočasný objekt základního typu objektu a inicializován inicializačním výrazem. Tento dočasný objekt je zničen okamžitě po zničení odkazu na objekt, ke kterému je vázán.|  
  
