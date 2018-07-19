---
title: Destruktory (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], destroying
- Visual C++, destructors
- destroying objects, destructors
- ~ operator [C++], specifying destructors
- destructors, about destructors
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bbe849f8ec9d47c73b7d909734df600957f3afd
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941782"
---
# <a name="destructors-c"></a>Destruktory (C++)

Destruktor je členská funkce, která je automaticky vyvolána při dostane mimo rozsah nebo zničen explicitně voláním objektu **odstranit**. Destruktor má stejný název jako třída předchází tildou (`~`). Například destruktor třídy `String` je deklarován jako: `~String()`.

Pokud není definován destruktor, kompilátor bude poskytovat výchozí; pro mnoho tříd to stačí. Potřebujete definovat vlastní destruktor třídy ukládá obslužné rutiny na systémové prostředky, které je potřeba uvolnit nebo ukazatele, které vlastníte paměť ukazují na.

Zvažte následující deklaraci třídy `String`:

```cpp
// spec1_destructors.cpp
#include <string.h>

class String {
public:
   String( char *ch );  // Declare constructor
   ~String();           //  and destructor.
private:
   char    *_text;
   size_t  sizeOfText;
};

// Define the constructor.
String::String( char *ch ) {
   sizeOfText = strlen( ch ) + 1;

   // Dynamically allocate the correct amount of memory.
   _text = new char[ sizeOfText ];

   // If the allocation succeeds, copy the initialization string.
   if( _text )
      strcpy_s( _text, sizeOfText, ch );
}

// Define the destructor.
String::~String() {
   // Deallocate the memory that was previously reserved
   //  for this string.
   if (_text)
      delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

V předchozím příkladu, destruktor `String::~String` používá **odstranit** Operátor navrácení dynamicky přidělené pro ukládání textu.

## <a name="declaring-destructors"></a>Deklarování destruktorů

Destruktory jsou funkce se stejným názvem jako třída, kterému ale předchází znak vlnovky (`~`)

Deklarace destruktorů se řídí několika pravidly. Destruktory:

- Nepřebírají argumenty.

- Nevrátí hodnotu (nebo **void**).

- Nelze deklarovat jako **const**, **volatile**, nebo **statické**. Nicméně lze vyvolat pro zničení objektů deklarovaných jako **const**, **volatile**, nebo **statické**.

- Lze deklarovat jako **virtuální**. Použitím virtuálních destruktorů lze zničit objekty bez znalosti jejich typu. Správný destruktor objektu je vyvolán pomocí mechanismu virtuální funkce. Destruktory lze také deklarovat jako čistě virtuální funkce pro abstraktní třídy.

## <a name="using-destructors"></a>Použití destruktorů

Destruktory jsou zavolány, pokud dojde k jedné z následujících událostí:

- Místní (automatický) objekt s rozsahem bloku se dostane mimo rozsah.

- Která byla objektu přidělena pomocí **nové** operátor je explicitně navrácena pomocí **odstranit**.

- Doba života dočasného objektu skončí.

- Program se ukončí a globální nebo statické objekty existují.

- Destruktor je explicitně zavolán pomocí plně kvalifikovaného názvu funkce destruktoru.

Destruktory mohou volně volat členské funkce třídy a přistupovat k datům člena třídy.

Existují dvě omezení týkající se použití destruktorů:

- Nelze převzít adresu.

- Odvozené třídy nedědí destruktorem základní třídy.

## <a name="order-of-destruction"></a>Pořadí odstranění

Pokud objekt dostane mimo rozsah nebo se odstraní, posloupnost událostí v její kompletní odstranění vypadá takto:

1. Je volán destruktor třídy a provede se tělo funkce destruktoru.

1. Destruktory pro nestatické členské objekty jsou volány v obráceném pořadí, v jakém jsou uvedeny v deklaraci třídy. Inicializační seznam volitelných členů použít v procesu vytváření těchto členů neovlivní pořadí konstrukci nebo destrukci.

1. Destruktory pro nevirtuální základní třídy jsou volány v obráceném pořadí deklarace.

1. Destruktory pro virtuální základní třídy jsou volány v obráceném pořadí deklarace.

```cpp
// order_of_destruction.cpp
#include <stdio.h>

struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };

struct B1      { ~B1() { printf("B1 dtor\n"); } };
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };

int main() {
   A1 * a = new A3;
   delete a;
   printf("\n");

   B1 * b = new B3;
   delete b;
   printf("\n");

   B3 * b2 = new B3;
   delete b2;
}

Output: A3 dtor
A2 dtor
A1 dtor

B1 dtor

B3 dtor
B2 dtor
B1 dtor

```

### <a name="virtual-base-classes"></a>Virtuální základní třídy

Destruktory pro virtuální základní třídy jsou volány v obráceném pořadí jejich výskytu orientovaného acyklického grafu (první hloubka, zleva doprava, postorder procházení). Následující obrázek znázorňuje grafu dědičnosti.

![Graf dědičnosti, který ukazuje virtuální základní třídy](../cpp/media/vc392j1.gif "vc392J1")

Graf dědičnosti s informacemi o virtuální třídy Base

Následuje seznam hlaviček třída pro třídy je vidět na obrázku.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Pro určení pořadí zničení virtuální základní třídy objektu typu `E`, kompilátor vytvoří seznam s použitím následující požadovaný algoritmus:

1. Procházet graf vlevo, počínaje nejhlubší bod v grafu (v tomto případě `E`).

1. Proveďte leftward procházení, dokud navštívili všechny uzly. Poznamenejte si název aktuální uzel.

1. Opakování v předchozím uzlu (dolů a doprava) a zjistěte, zda je uzel se uloží virtuální základní třídy.

1. Pokud zapamatovaných uzel je virtuální základní třídy, vyhledejte v seznamu zobrazíte, zda je již byl zadán. Pokud není virtuální základní třídy, ji ignorujte.

1. Pokud zapamatovaných uzel ještě není v seznamu, přidejte ho do dolní části seznamu.

1. Procházet graf úložišti a na následující cestě vpravo.

1. Přejděte ke kroku 2.

1. Když se vyčerpá poslední stoupající cestu, poznamenejte si název aktuální uzel.

1. Přejděte ke kroku 3.

1. Tomto procesu pokračujte, dokud nebude uzel dolů opět aktuální uzel.

Proto pro třídu `E`, pořadí zničení je:

1. Nevirtuální základní třídy `E`.

1. Nevirtuální základní třídy `D`.

1. Nevirtuální základní třídy `C`.

1. Virtuální základní třídy `B`.

1. Virtuální základní třídy `A`.

Tento proces vytvoří seřazený seznam jedinečných položek. Bez názvu třídy vyskytuje dvakrát. Jakmile je vytvořen v seznamu, je v obráceném pořadí vás a je volán destruktor pro každou ze tříd v seznamu od posledního první.

Pořadí konstrukci nebo destrukci je primárně důležité, pokud konstruktory a destruktory jedné třídy využívají jiné součásti vytváří první nebo ukládání už – například pokud destruktor `A` (na obrázku výše uvedené) spoléhali na `B` stále k dispozici při provádění jeho kód, nebo naopak.

Takové vzájemné závislosti mezi třídami v grafu dědičnosti jsou ze své podstaty nebezpečné, protože třídy odvozené později můžete měnit což je úplně vlevo cestu, a tím změnit pořadí konstrukce a zničení.

### <a name="non-virtual-base-classes"></a>Nevirtuální základní třídy

Destruktory pro nevirtuální základní třídy jsou volány v obráceném pořadí, ve kterém jsou deklarovány název základní třídy. Zvažte následující deklaraci třídy:

```cpp
class MultInherit : public Base1, public Base2
...
```

V předchozím příkladu, destruktor `Base2` je volána před provedením destruktor `Base1`.

## <a name="explicit-destructor-calls"></a>Explicitní volání destruktoru

Explicitní volání destruktoru je zřídka nezbytné. Avšak může být užitečné pro vyčištění objektů umístěných na absolutních adresách. Tyto objekty jsou obvykle přiděleny pomocí uživatelem definované **nové** operátor, který přijímá argument umístění. **Odstranit** operátor nemůže navrátit tuto paměť, protože není přidělena z volného úložiště (Další informace najdete v tématu [nové a odstranit operátory](../cpp/new-and-delete-operators.md)). Volání destruktoru však může provádět odpovídající vyčištění. Chcete-li explicitně zavolat destruktor objektu `s` třídy `String`, použijte jeden z následujících příkazů:

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

Zápis explicitního volání destruktorů, ukázaný v předchozím příkladu, lze použít bez ohledu na to, zda typ destruktor definuje. To umožňuje provést explicitní volání bez znalosti, zda je definován destruktor typu. Explicitní volání destruktoru, který není definován, nemá žádný vliv.
