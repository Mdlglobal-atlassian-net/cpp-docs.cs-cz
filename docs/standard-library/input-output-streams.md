---
title: Vstupně výstupní streamy
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: d426baacb52095ab2d933263fdac8e312fc29558
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580215"
---
# <a name="inputoutput-streams"></a>Vstupní/výstupní datové proudy

`basic_iostream`, která je definována v hlavičkovém souboru \<istream >, je šablona třídy pro objekty, které obě zpracování vstupu a výstupu znakový vstupně-výstupních operací datové proudy.

Existují dvě definice typedefs jazyka, které definují konkrétní znak specializace `basic_iostream` a může pomoct, aby byl kód lépe čitelný: `iostream` (Nezaměňovat s hlavičkový soubor \<iostream – >) vstupně-výstupních operací datový proud, který je založen na `basic_iostream<char>`; `wiostream` vstupně-výstupních operací datový proud, který je založen na `basic_iostream<wchar_t>`.

Další informace najdete v tématu [basic_iostream – třída](../standard-library/basic-iostream-class.md), [iostream –](../standard-library/basic-iostream-class.md), a [wiostream](../standard-library/basic-iostream-class.md).

Odvozování z `basic_iostream` je šablona třídy `basic_fstream`, který se používá k datového proudu znaků dat do a ze souborů.

Existují také definice TypeDef, která poskytují konkrétní znak specializace `basic_fstream`. Jsou `fstream`, což je datový proud souboru vstupně-výstupní operace, která je založena na **char**, a `wfstream`, což je datový proud souboru vstupně-výstupní operace, která je založena na **wchar_t**. Další informace najdete v tématu [basic_fstream – třída](../standard-library/basic-fstream-class.md), [fstream –](../standard-library/basic-fstream-class.md), a [wfstream](../standard-library/basic-fstream-class.md). Použití tyto funkce TypeDef vyžaduje zahrnutí souboru hlaviček \<fstream – >.

> [!NOTE]
> Když `basic_fstream` objektu se používá k provedení vstup a výstup souborů, i když základní vyrovnávací paměť obsahuje samostatně určené pozice pro čtení a zápis, aktuální vstup a aktuální pozice výstup spojených dohromady, a proto čtení některá data přesouvá umístění výstupu.

Šablona třídy `basic_stringstream` a jeho běžné specializace `stringstream`, často se používají k práci s objekty vstupně-výstupních operací datového proudu pro vložení a extrahovat znaková data. Další informace najdete v tématu [basic_stringstream – třída](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Viz také:

[stringstream](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream – třída](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream >](../standard-library/sstream.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
