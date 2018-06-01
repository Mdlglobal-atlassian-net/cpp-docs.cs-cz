---
title: Oddělovače pro dokumentační značky jazyka Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe65dfec3befa15ffebde3d074081ee11364f4d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33337571"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Oddělovače pro dokumentační značky ve Visual C++
Použití značky dokumentace vyžaduje oddělovače, které označují kompilátoru kde komentáře dokumentace k zahájení a ukončení.  
  
 Můžete použít následující typy oddělovače s dokumentační značky XML:  
  
 `///`  
 Toto je formulář, který je zobrazeno v příkladech dokumentace a použít šablony projektů Visual C++.  
  
 `/** */`  
 Jedná se o Víceřádkový oddělovače.  
  
 Existují některé formátování pravidla při použití `/** */` oddělovače:  
  
-   Pro řádek, který obsahuje `/**` oddělovač, pokud zbývající řádku je prázdné znaky, řádek není zpracován pro komentáře. Pokud je první znak mezer, že prázdný znak je ignorován a zbytek řádku je zpracovat. V opačném celý text řádku po `/**` oddělovač zpracovávány jako součást komentář.  
  
-   Pro řádek, který obsahuje `*/` oddělovač, pokud je pouze mezera až `*/` oddělovač, daného řádku je ignorováno. Jinak hodnota textu v řádku než `*/` oddělovač zpracovávány jako součást komentář, dodržování pravidel porovnávání popsané v následující odrážka.  
  
-   Řádků po ten, který začíná `/**` oddělovač, kompilátor hledá společný vzorek na začátku každého řádku, která se skládá z mezer volitelné a znak hvězdičky (`*`), za nímž následují další volitelné mezer. Pokud kompilátor najde společnou sadu znaků na začátku každého řádku, se budou ignorovat tento vzor pro všechny řádky po `/**` oddělovač, než a případně včetně řádek, který obsahuje `*/` oddělovač.  
  
 Příklady:  
  
-   Část pouze následující komentář, který bude zpracován je řádek, který začíná `<summary>`. Následující formáty dvě značky vytvoří stejné komentáře:  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   Kompilátor použije vzorec "*" Ignorovat na začátku druhé a třetí řádky.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   Kompilátor vyhledá žádné vzor v tohoto komentáře, protože neexistuje žádný hvězdičky na druhém řádku. Proto veškerý text na řádcích druhé a třetí až do `*/`, budou zpracovány jako součást komentář.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   Kompilátor vyhledá žádné vzor v tohoto komentáře dvou důvodů. První je žádný řádek, který začíná konzistentní počet mezer před hvězdičku. Druhý páté řádek začíná na kartě, který neodpovídá prostory. Proto všechny text z druhého řádku až `*/` budou zpracovány jako součást komentář.  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)