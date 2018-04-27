---
title: Navigace v systému souborů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 999814a0d70e0c8a29767bd98c7f7b0ea0c91557
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="file-system-navigation"></a>Navigace v systému souborů

\<Filesystem > záhlaví implementuje 18822:2015 C++ souboru systému Technical specifikace ISO/IEC TS (konečné koncept: [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)) a má typy a funkce, které vám umožní zápisu nezávislé na platformě kód pro navigaci systému souborů. Protože je napříč platformami, obsahuje rozhraní API, která nejsou důležité pro systémy Windows. Například to znamená, že `is_fifo(const path&)` vždy vrátí hodnotu `false` v systému Windows.

## <a name="overview"></a>Přehled

Použití \<filesystem > rozhraní API pro následující úkoly:

- iterace souborů a adresářů v zadané cestě

- získání informací o souborech, včetně v době vytvoření, velikost, rozšíření a kořenový adresář

- Napište, rozložit a porovnání cest

- Vytvoření, kopírování a odstranění adresáře

- Zkopírujte a odstranit soubory

Další informace o vstupně-výstupní soubor pomocí standardní knihovny najdete v tématu [iostream – programování](../standard-library/iostream-programming.md).

## <a name="paths"></a>Cesty

### <a name="constructing-and-composing-paths"></a>Sestavování a skládání cesty

Cesty v systému Windows (od XP) jsou nativně uložené ve formátu Unicode. [Cesta](../standard-library/path-class.md) třída automaticky provede všechny potřebné řetězec převody. Přijímá argumenty obou široké a úzké znaková pole, a také `std::string` a `std::wstring` typů formátu UTF8 nebo UTF16. `path` Třída taky automaticky normalizuje cestu oddělovačů. Můžete vytvořit jeden lomítkem za oddělovač adresářů v argumenty konstruktoru. To umožňuje používat stejné řetězce pro uložení cest v prostředích Windows a UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Ke zřetězení dvě cesty, můžete použít přetížené `/` a `/=` operátory, které jsou obdobou `+` a `+=` operátory na `std::string` a `std::wstring`. `path` Objektu bude pohodlně zadat oddělovače, pokud to neuděláte.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Zkoumání cesty

Třída cesta obsahuje několik metod, které vracejí informace o různých částí od entity systému souborů, které může odkazovat na sebe, cesty. Můžete získat kořenové, relativní cesta, název souboru, přípona souboru a další. Můžete iterace v cesty objektu prozkoumat všechny složky v hierarchii. Následující příklad ukazuje, jak pro iteraci prostřednictvím cesty (ne adresář, který odkazuje na) a načíst informace o jejích částí.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

void main(int argc, char* argv[])
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Kód vytvoří tento výstup:

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>Porovnání cest

`path` Třída přetížení stejné operátory porovnání jako `std::string` a `std::wstring`. Při porovnávání dvě cesty provádění porovnání řetězců po mít byla normalized oddělovače. Pokud chybí koncové lomítko (nebo zpětné lomítko) nebyla přidána a ovlivňuje porovnání. Následující příklad ukazuje, jak porovnat hodnoty cesta:

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

Pokud chcete spustit tento kód, vložte jej do úplné výše uvedeného příkladu před `main` a zrušte komentář u řádku, který volá v hlavní.

### <a name="converting-between-path-and-string-types"></a>Převod mezi typy cestu a řetězce

A `path` je implicitně převést na objekt `std::wstring` nebo `std::string`. To znamená, že je cesta předat do funkce, jako [wofstream::open](../standard-library/basic-ofstream-class.md#open), jak je uvedeno v následujícím příkladu:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

void main(int argc, char* argv[])
{
    wchar_t* p = L"C:/Users/Public/Documents";
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>Iterace adresářů a souborů

\<Filesystem > záhlaví poskytuje [directory_iterator](../standard-library/directory-iterator-class.md) typ Iterujte přes jednoho adresáře a [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) třída iterace rekurzivně adresář a jejích podadresářů. Po sestavení iterovat předáním ho `path` objektu iteraci odkazuje na první directory_entry v cestě. Vytvořte end iterator voláním výchozí konstruktor.

Když iterace v rámci adresáře, existuje několik typů položek, které se můžete setkat, včetně mimo jiné adresáře, soubory, symbolické odkazy a soubory soketu. `directory_iterator` Vrátí jeho položky jako [directory_entry](../standard-library/directory-entry-class.md) objekty.
