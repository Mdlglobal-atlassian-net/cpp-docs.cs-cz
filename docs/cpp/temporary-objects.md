---
title: Dočasné objekty
ms.date: 11/04/2016
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
ms.openlocfilehash: b298872a688c3b8e383a04ea4d82753859cbb2e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160746"
---
# <a name="temporary-objects"></a>Dočasné objekty

V některých případech je pro kompilátor nezbytné vytvořit dočasné objekty. Tyto dočasné objekty mohou být vytvořeny z následujících důvodů:

- Pro inicializaci odkazu **const** s inicializátorem jiného typu než v nadřazeném typu odkazu, který se má inicializovat.

- Uložení návratové hodnoty funkce, která vrací uživatelský typ. Tyto dočasné objekty jsou vytvořeny pouze v případě, že program nekopíruje hodnotu vrácenou objektu. Příklad:

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   Protože vrácená hodnota není do jiného objektu zkopírována, je vytvořen dočasný objekt. Častější případ, kdy jsou dočasné objekty vytvořeny, je při vyhodnocení výrazu, kde musí být volány funkce přetíženého operátoru. Tyto funkce přetíženého operátoru vrátí uživatelský typ, který často není zkopírován do jiného objektu.

   Vezměte v úvahu výraz `ComplexResult = Complex1 + Complex2 + Complex3`. Výraz `Complex1 + Complex2` je vyhodnocen a výsledek je uložen v dočasném objektu. Dále je vyhodnocen *dočasný* `+ Complex3` výrazu a výsledek je zkopírován do `ComplexResult` (za předpokladu, že operátor přiřazení není přetížený).

- Uložení výsledku přetypování do uživatelského typu. Když je objekt daného typu explicitně převeden na uživatelský typ, tento nový objekt je zkonstruován jako dočasný objekt.

Dočasné objekty mají dobu života, která je definována bodem jejich vytvoření a bodem, ve kterém jsou zničeny. Libovolný výraz, který vytvoří více než jeden dočasný objekt, je nakonec zničí v obráceném pořadí, než ve kterém byly vytvořeny. Body, ve kterých dochází ke zničení, jsou uvedeny v následující tabulce.

### <a name="destruction-points-for-temporary-objects"></a>Body zničení dočasných objektů

|Důvod vytvoření dočasného objektu|Bod zničení|
|------------------------------|-----------------------|
|Výsledek vyhodnocení výrazu|Všechny dočasné objekty vytvořené v důsledku vyhodnocení výrazu jsou zničeny na konci příkazu výrazu (tj. středníkem) nebo na konci řídicích výrazů pro příkazy **for**, **if** **,** **while**a **Switch** .|
|Inicializace odkazů **const**|Pokud není inicializátorem l-hodnota stejného typu jako inicializovaný odkaz, je vytvořen dočasný objekt základního typu objektu a inicializován inicializačním výrazem. Tento dočasný objekt je zničen okamžitě po zničení odkazu na objekt, ke kterému je vázán.|
