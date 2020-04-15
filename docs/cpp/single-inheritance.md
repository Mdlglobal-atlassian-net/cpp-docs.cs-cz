---
title: Jedna dědičnost
ms.date: 11/19/2018
helpviewer_keywords:
- single inheritance
- base classes [C++], indirect
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- derived classes [C++], single base class
- inheritance, single
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
ms.openlocfilehash: 8fe141886fd5087b71484368c0f79d62238f7f22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365616"
---
# <a name="single-inheritance"></a>Jedna dědičnost

V „jednoduché dědičnosti“, tedy v běžné formě dědičnosti, mají třídy pouze jednu základní třídu. Vezměte v úvahu vztah znázorněný na následujícím obrázku.

![Graf základní&#45;dědičnosti](../cpp/media/vc38xj1.gif "Graf základní&#45;dědičnosti") <br/>
Jednoduchý graf jednoduché dědičnosti

V obrázku si povšimněte přechodu od obecného ke konkrétnímu. Další běžnou vlastností návrhu ve většině hierarchií tříd je, že odvozené třídy mají se základní třídou vztah „je druh“. V obrázku je třída `Book` druhem třídy `PrintedDocument` a třída `PaperbackBook` je druhem třídy `book`.

Na obrázku si lze povšimnout ještě jedné položky: třída `Book` je odvozenou třídou (z třídy `PrintedDocument`) a zároveň základní třídou (třída `PaperbackBook` je odvozena z třídy `Book`). Základní deklarace takové hierarchie tříd je uvedena v následujícím příkladu:

```cpp
// deriv_SingleInheritance.cpp
// compile with: /LD
class PrintedDocument {};

// Book is derived from PrintedDocument.
class Book : public PrintedDocument {};

// PaperbackBook is derived from Book.
class PaperbackBook : public Book {};
```

Třída `PrintedDocument` je považována za „přímou základní“ třídu třídy `Book`. Je „nepřímo základní“ třídou třídy `PaperbackBook`. Rozdílem je, že přímá základní třída se vyskytuje v seznamu základních tříd deklarace třídy, zatímco nepřímá základní třída nikoli.

Základní třída, ze které je každá třída odvozena, je deklarována před deklarací odvozené třídy. Nepostačuje poskytnout vpřed odkazující deklaraci pro základní třídu, musí jít o úplnou deklaraci.

V předchozím příkladu **se** používá veřejný specifikátor přístupu. Význam veřejné, chráněné a soukromé dědičnosti je popsán v [řízení přístupu členů.](../cpp/member-access-control-cpp.md)

Jak ukazuje následující obrázek, třída může sloužit jako základní třída mnoha specifickým třídám.

![Řízený acyklický graf](../cpp/media/vc38xj2.gif "Řízený acyklický graf") <br/>
Ukázka orientovaného acyklického grafu

Ve výše uvedeném diagramu nazývaném „orientovaný acyklický graf“ (také „DAG“) jsou některé třídy základními třídami více než jedné odvozené třídy. Opačně to však neplatí: každá odvozená třída má pouze jednu přímou základní třídu. Graf na obrázku znázorňuje strukturu „jednoduché dědičnosti“.

> [!NOTE]
> Orientované acyklické grafy se nepoužívají pouze pro jednoduchou dědičnost. Používají se také ke znázornění grafů vícenásobné dědičnosti.

V dědičnosti obsahuje odvozená třída členy základní třídy a nové, přidané členy. Díky tomu mohou odvozené třídy odkazovat na členy základní třídy (pokud tyto členy nebyly v odvozené třídě předefinovány). Pokud byly členy v odvozené třídě předefinovány, lze se na členy v přímých nebo nepřímých základních třídách odkazovat pomocí operátoru vyhodnocení oboru (`::`). Vezměme si tento příklad:

```cpp
// deriv_SingleInheritance2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;
class Document {
public:
   char *Name;   // Document name.
   void PrintNameOf();   // Print name.
};

// Implementation of PrintNameOf function from class Document.
void Document::PrintNameOf() {
   cout << Name << endl;
}

class Book : public Document {
public:
   Book( char *name, long pagecount );
private:
   long  PageCount;
};

// Constructor from class Book.
Book::Book( char *name, long pagecount ) {
   Name = new char[ strlen( name ) + 1 ];
   strcpy_s( Name, strlen(Name), name );
   PageCount = pagecount;
};
```

Povšimněte si, že konstruktor třídy `Book` (`Book::Book`) má přístup k datovému členu `Name`. Objekt typu `Book` lze v programu vytvořit a použít takto:

```cpp
//  Create a new object of type Book. This invokes the
//   constructor Book::Book.
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );

...

//  Use PrintNameOf function inherited from class Document.
LibraryBook.PrintNameOf();
```

Jak ukazuje předchozí příklad, členy třídy a zděděná data a funkce se používají zcela shodně. Vyžaduje-li implementace třídy `Book` novou implementaci funkce `PrintNameOf`, lze funkci patřící třídě `Document` volat pouze pomocí operátoru vyhodnocení oboru (`::`):

```cpp
// deriv_SingleInheritance3.cpp
// compile with: /EHsc /LD
#include <iostream>
using namespace std;

class Document {
public:
   char *Name;          // Document name.
   void  PrintNameOf() {}  // Print name.
};

class Book : public Document {
   Book( char *name, long pagecount );
   void PrintNameOf();
   long  PageCount;
};

void Book::PrintNameOf() {
   cout << "Name of book: ";
   Document::PrintNameOf();
}
```

Existuje-li přístupná a jednoznačná základní třída, lze ukazatele a reference na odvozené třídy implicitně převádět na ukazatele a reference jejich základní třídy. Následující kód tento koncept demonstruje pomocí ukazatelů (pro reference platí stejný princip):

```cpp
// deriv_SingleInheritance4.cpp
// compile with: /W3
struct Document {
   char *Name;
   void PrintNameOf() {}
};

class PaperbackBook : public Document {};

int main() {
   Document * DocLib[10];   // Library of ten documents.
   for (int i = 0 ; i < 5 ; i++)
      DocLib[i] = new Document;
   for (int i = 5 ; i < 10 ; i++)
      DocLib[i] = new PaperbackBook;
}
```

V předchozím příkladu jsou vytvořeny různé typy. Protože jsou však všechny tyto typy odvozeny ze třídy `Document`, provádí se implicitní převod na typ `Document *`. V důsledku toho je objekt `DocLib` „heterogenní seznam“ (seznam, v němž objekty nejsou všechny stejného typu) obsahující různé druhy objektů.

Jelikož třída `Document` obsahuje funkci `PrintNameOf`, dokáže vypsat názvy všech knih v knihovně, přestože může vynechat některé informace specifické pro daný typ dokumentu (počet stran u objektů `Book`, počet bajtů u objektu `HelpFile` atd.).

> [!NOTE]
> Často není optimální přinutit základní třídu implementovat funkci jako `PrintNameOf`. [Virtuální funkce](../cpp/virtual-functions.md) nabízí další alternativy návrhu.
