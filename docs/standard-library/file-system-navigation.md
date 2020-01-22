---
title: Navigace v systému souborů
ms.date: 11/04/2016
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: ea9bf44a11087180d3bd02c5dcd5d1acfa4b9e57
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518501"
---
# <a name="file-system-navigation"></a>Navigace v systému souborů

Hlavička > \<systému C++ souborů implementuje technickou specifikaci systému souborů ISO/IEC TS 18822:2015 (finální koncept: [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)) a má typy a funkce, které umožňují psát kód nezávislý na platformě pro navigaci v systému souborů. Vzhledem k tomu, že se jedná o různé platformy, obsahuje rozhraní API, která nejsou relevantní pro systémy Windows. To například znamená, že `is_fifo(const path&)` vždy vrátí **hodnotu false** ve Windows.

## <a name="overview"></a>Přehled

Pro následující úlohy použijte rozhraní API pro \<> systému souborů:

- Iterujte přes soubory a adresáře v zadané cestě.

- získat informace o souborech, včetně času vytvoření, velikosti, rozšíření a kořenového adresáře

- vytváření, rozložit a porovnat cesty

- vytváření, kopírování a odstraňování adresářů

- kopírování a odstraňování souborů

Další informace o souborových vstupně-výstupních operacích pomocí standardní knihovny najdete v tématu [iostream – Programming](../standard-library/iostream-programming.md).

## <a name="paths"></a>Cesty

### <a name="constructing-and-composing-paths"></a>Vytváření a sestavování cest

Cesty ve Windows (od verze XP) se ukládají nativně v kódování Unicode. Třída [path](../standard-library/path-class.md) automaticky provede všechny potřebné převody řetězců. Přijímá argumenty pro rozsáhlá i úzká znaková pole a také `std::string` a `std::wstring` typy naformátované jako UTF8 nebo UTF16. Třída `path` také automaticky normalizuje oddělovače cest. V argumentech konstruktoru můžete jako oddělovač adresářů použít jedno lomítko. To umožňuje použít stejné řetězce pro ukládání cest v prostředích Windows i UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Pro zřetězení dvou cest můžete použít přetížené operátory `/` a `/=`, které jsou podobné operátorům `+` a `+=` na `std::string` a `std::wstring`. Objekt `path` vhodným způsobem dodá oddělovače, pokud to neuděláte.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Prozkoumání cest

Třída path má několik metod, které vracejí informace o různých částech samotné cesty, jako oddělené od entity systému souborů, na kterou se může odkazovat. Můžete získat kořen, relativní cestu, název souboru, příponu souboru a další. Můžete iterovat přes objekt cesty a prozkoumávat všechny složky v hierarchii. Následující příklad ukazuje, jak iterovat cestu (ne adresář, na který odkazuje), a načítat informace o jeho částech.

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

int main(int argc, char* argv[])
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

### <a name="comparing-paths"></a>Porovnávání cest

Třída `path` přetěžuje stejné operátory porovnávání jako `std::string` a `std::wstring`. Při porovnání dvou cest provádíte porovnávání řetězců poté, co byly oddělovače normalizovány. Pokud koncové lomítko (nebo zpětné lomítko) chybí, není přidáno a ovlivňuje porovnání. Následující příklad ukazuje, jak se hodnoty cest rovnají:

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

Chcete-li spustit tento kód, vložte jej do úplného příkladu výše před `main` a odkomentujte řádek, který ho volá v rámci Main.

### <a name="converting-between-path-and-string-types"></a>Převod mezi cestou a typy řetězců

Objekt `path` lze implicitně převést na `std::wstring` nebo `std::string`. To znamená, že můžete předat cestu k funkcím, jako je například [wofstream:: Open](../standard-library/basic-ofstream-class.md#open), jak je znázorněno v následujícím příkladu:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

int main(int argc, char* argv[])
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

Hlavička > \<systému souborů poskytuje [Directory_iterator](../standard-library/directory-iterator-class.md) typ pro iteraci přes jednotlivé adresáře a třídu [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pro rekurzivní iteraci přes adresář a jeho podadresáře. Po vytvoření iterátoru předáním `path` objektu, iterátor ukazuje na první directory_entry v cestě. Vytvořte koncový iterátor voláním výchozího konstruktoru.

Při iteraci v adresáři existuje několik druhů položek, které mohou nastat, mimo jiné adresáře, soubory, symbolické odkazy a soubory soketu. `directory_iterator` vrátí své položky jako objekty [directory_entry](../standard-library/directory-entry-class.md) .
