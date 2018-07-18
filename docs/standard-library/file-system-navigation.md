---
title: Navigace v systému souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e6e14e0b94000972873b6050f0e8154891b4e57
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026796"
---
# <a name="file-system-navigation"></a>Navigace v systému souborů

\<Systému souborů > záhlaví implementuje 18822:2015 C++ souboru systému technické specifikace ISO/IEC TS (konečný návrh: [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)) a má typy a funkce, které umožňují zapisovat nezávislá na platformě kód pro navigaci v systému souborů. Protože je multiplatformní, obsahuje rozhraní API, která nejsou relevantní pro systémy Windows. Například to znamená, že `is_fifo(const path&)` vždy vrátí **false** na Windows.

## <a name="overview"></a>Přehled

Použití \<filesystem > rozhraní API pro následující úlohy:

- Iterujte přes soubory a adresáře zadané cestě.

- získání informací o souborech, včetně čas vytvoření, velikost, rozšíření a kořenový adresář

- Sestavujte, rozložení a porovnat cesty

- vytváření, kopírování a odstraňujte adresáře

- Zkopírujte a odstranit soubory

Další informace o v/v souborů pomocí standardní knihovny najdete v tématu [iostream – programování](../standard-library/iostream-programming.md).

## <a name="paths"></a>Cesty

### <a name="constructing-and-composing-paths"></a>Sestavování a vytváření cesty

Cesty ve Windows (od verze XP) jsou uloženy nativně v kódování Unicode. [Cesta](../standard-library/path-class.md) třídy automaticky provede všechny převody potřebné řetězec. Přijímá argumenty obou široké a úzkými znaky pole, stejně jako `std::string` a `std::wstring` typů formátu UTF8 nebo UTF16. `path` Třídy také automaticky normalizuje cestu oddělovače. Jeden lomítkem slouží jako oddělovač adresáře v argumentech konstruktoru. To umožňuje používat stejné řetězce pro uložení cest v prostředí Windows a UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Ke zřetězení dvou možných cest, můžete použít přetížené `/` a `/=` operátory, které jsou obdobou `+` a `+=` operátory na `std::string` a `std::wstring`. `path` Objektu bude jednoduše zadat oddělovače, pokud to neuděláte.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Zkoumání cesty

Cesta třídy má několik metod, které vracejí informace o různých částech cesty k samotné odlišuje entitu systému souboru, kterou může odkazovat na. Můžete získat kořenový adresář, relativní cesty, názvu souboru, přípona souboru a další. Můžete iterovat přes objekt cesty ke kontrole všechny složky v hierarchii. Následující příklad ukazuje, jak k iteraci přes cestu (ne adresář, který odkazuje na) a k načtení informací o jejích částí.

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

`path` Třídy přetížení stejné operátory porovnání jako `std::string` a `std::wstring`. Při porovnávání dvou možných cest fungují po oddělovače mají normalizované. porovnání řetězců. Pokud chybí koncové lomítko (nebo zpětné lomítko) není přidán a má vliv na porovnání. Následující příklad ukazuje, jak porovnat hodnoty cest:

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

Chcete-li spustit tento kód, vložte ho do Úplný příklad výše před `main` a zrušte komentář u řádku, který volá ve funkci main.

### <a name="converting-between-path-and-string-types"></a>Převod mezi typy cesty a řetězce

A `path` je implicitně převést na objekt `std::wstring` nebo `std::string`. To znamená, že cestu můžete předat do funkce, jako [wofstream::open](../standard-library/basic-ofstream-class.md#open), jak je znázorněno v tomto příkladu:

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

\<Systému souborů > obsahuje záhlaví [directory_iterator –](../standard-library/directory-iterator-class.md) typu k iteraci přes jednoho adresáře a [recursive_directory_iterator –](../standard-library/recursive-directory-iterator-class.md) třídy rekurzivně iteraci adresář a jeho podadresářích. Poté, co ji vytvoříte iterátor `path` objektu, odkazuje iterátor na první directory_entry – v cestě. Vytvořte koncový iterátor volání výchozího konstruktoru.

Při procházení adresáře, existuje několik typů položek, které se můžete setkat, včetně, ale nikoli výhradně, adresářů, souborů, symbolické odkazy a soubory soketu. `directory_iterator` Vrátí jeho položky jako [directory_entry –](../standard-library/directory-entry-class.md) objekty.
