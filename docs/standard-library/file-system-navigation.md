---
title: Navigace v systému souborů
description: Jak se k navigaci v systému souborů pomocí souborů c++ standard usměrňovat.
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 412d865582a14da7b8c31d9f07a43106b0c49491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368430"
---
# <a name="file-system-navigation"></a>Navigace v systému souborů

Záhlaví \<souborového systému> implementuje technickou specifikaci souborového systému C++ISO/IEC TS 18822:2015 (konečný koncept: [ISO/IEC JTC 1/SC 22/WG 21 N4100)](https://wg21.link/n4100)a má typy a funkce, které vám umožní psát kód nezávislý na platformě pro navigaci v systému souborů. Vzhledem k tomu, že je multiplatformní, obsahuje api, které nejsou relevantní pro systémy Windows. Například `is_fifo(const path&)` vždy vrátí **false** v systému Windows.

## <a name="overview"></a>Přehled

Pomocí \<souborů> API pro následující úkoly:

- iterate přes soubory a adresáře pod zadanou cestou

- získání informací o souborech včetně vytvořeného času, velikosti, rozšíření a kořenového adresáře

- skládat, rozkládat a porovnávat cesty

- vytváření, kopírování a odstraňování adresářů

- kopírování a odstraňování souborů

Další informace o vzpona souboru pomocí standardní knihovny naleznete v [tématu iostream Programming](../standard-library/iostream-programming.md).

## <a name="paths"></a>Cesty

### <a name="constructing-and-composing-paths"></a>Vytváření a vytváření cest

Cesty v systému Windows (protože XP) jsou uloženy nativně v Unicode. Třída [cesty](../standard-library/path-class.md) automaticky provádí všechny potřebné převody řetězců. Přijímá argumenty širokých i úzkých polí znaků `std::string` `std::wstring` a obou typů a typů formátovaných jako UTF8 nebo UTF16. Třída `path` také automaticky normalizuje oddělovače cest. Jedno lomítko můžete použít jako oddělovač adresářů v argumentech konstruktoru. Tento oddělovač umožňuje používat stejné řetězce k ukládání cest v prostředí systému Windows i unixu:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Chcete-li zřetězit dvě cesty, můžete `/` použít `/=` přetížené a operátory, `+` `+=` které `std::string` jsou `std::wstring`podobné a operátory na a . Objekt `path` bude pohodlně dodávat oddělovače, pokud tak neučiníte.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Zkoumání cest

Třída cesta má několik metod, které vracejí informace o různých částech samotné cesty. Tyto informace se liší od informací o entitě systému souborů, na kterou se mohou odkazovat. Můžete získat kořen, relativní cestu, název souboru, příponu souboru a další. Můžete iterate přes objekt cesty prozkoumat všechny složky v hierarchii. Následující příklad ukazuje, jak iterate přes objekt cesty. A jak získat informace o jeho částech.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

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

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Kód vytváří tento výstup:

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

Třída `path` přetížení stejné operátory `std::string` porovnání `std::wstring`jako a . Při porovnání dvou cest provedete porovnání řetězců po normalizování oddělovačů. Pokud koncové lomítko (nebo zpětné lomítko) chybí, není přidáno a to má vliv na porovnání. Následující příklad ukazuje, jak porovnat hodnoty cesty:

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

Chcete-li spustit tento kód, vložte `main` jej do úplného příkladu výše před a odkomentujte řádek, který jej volá v main.

### <a name="converting-between-path-and-string-types"></a>Převod mezi typy cest a řetězců

Objekt `path` je implicitně `std::wstring` převoditelný na nebo `std::string`. To znamená, že můžete předat cestu k funkcím, jako je [wofstream::open](../standard-library/basic-ofstream-class.md#open), jak je znázorněno v tomto příkladu:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
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

Záhlaví \<> souborového systému poskytuje typ [directory_iterator](../standard-library/directory-iterator-class.md) pro iterace přes jednotlivé adresáře a [třída recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pro rekurzivně itrekurzi přes adresář a jeho podadresáře. Po vytvoření iterátoru předáním `path` objektu, iterátor odkazuje na první directory_entry v cestě. Vytvořte koncový iterátor voláním výchozího konstruktoru.

Při iterace prostřednictvím adresáře existuje několik druhů položek, které můžete zjistit. Mezi tyto položky patří adresáře, soubory, symbolické odkazy, soubory soketu a další. Vrátí `directory_iterator` své položky jako [directory_entry](../standard-library/directory-entry-class.md) objekty.
