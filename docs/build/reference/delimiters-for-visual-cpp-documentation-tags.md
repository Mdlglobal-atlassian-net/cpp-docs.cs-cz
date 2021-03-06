---
title: Oddělovače pro dokumentační komentáře ve Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
ms.openlocfilehash: a5a0534ba74cc9b125e94d4ece133c2449700a67
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446539"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Oddělovače pro dokumentační komentáře ve Visual C++

Použití dokumentační značky vyžaduje oddělovače, které označují kompilátoru kde Dokumentační komentář začíná a končí.

Můžete použít následující typy oddělovače se značkami dokumentace XML:

| | |
|-|-|
| `///` | Toto je formulář, který je znázorněno v příkladu v dokumentaci se používá sada Visual Studio C++ šablony projektu.  |
| `/** */`  | Jedná se o Víceřádkový oddělovače.  |

Existují některé formátování při použití pravidla `/** */` oddělovače:

- Pro řádek, který obsahuje `/**` oddělovač, pokud zbytek řádku je prázdný znak řádku není zpracovávána pro poznámky. Pokud je první znak prázdným znakem, že znak bílého prostoru řádku je ignorován a zbytek řádku je zpracovat. V opačném případě celý text řádku po `/**` oddělovač zpracovávány jako součást komentář.

- Pro řádek, který obsahuje `*/` oddělovač, pokud existuje jenom prázdné znaky až `*/` oddělovač, tento řádek se ignoruje. V opačném případě text na řádku až `*/` oddělovač zpracovávány jako součást komentář porovnávání vzorů podle pravidel popsaných v následující odrážky.

- Pro řádky za ten, který začíná `/**` oddělovač, hledá kompilátor běžný vzor na začátku každého řádku, který se skládá z volitelné prázdné místo a hvězdičku (`*`) a po něm další volitelné prázdné znaky. Pokud kompilátor najde společnou sadu znaků na začátku každého řádku, bude ignorovat tento vzor pro všechny řádky za `/**` oddělovač, až po a pravděpodobně včetně řádek, který obsahuje `*/` oddělovač.

Příklady:

- Řádek, který začíná je jediná součást následující komentář, který se zpracuje `<summary>`. Následující dvě značky formáty vytvoří stejný komentáře:

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- Kompilátor použije vzor " \* " na začátku druhé a třetí řádky ignorovat.

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- Kompilátor najde žádný vzor v tento komentář, protože neexistuje žádný hvězdičku na druhém řádku. Proto se veškerý text na řádcích druhé a třetí až do `*/`, bude zpracována jako součást komentář.

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- Kompilátor vyhledá žádný model v tento komentář dvou důvodů. Nejprve neexistuje žádný řádek, který začíná konzistentní počet mezer před hvězdičku. Za druhé pátý řádek začíná kartu, která se neshoduje s mezery. Proto veškerý text z druhého řádku až `*/` se zpracuje jako součást komentář.

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
