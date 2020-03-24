---
title: Konstruktory a operátory přiřazení pro kopírování (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: beabe4c6219975d33c7af98a94498188c9abfa55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189525"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Konstruktory a operátory přiřazení pro kopírování (C++)

> [!NOTE]
> Počínaje jazykem C++ 11 se v jazyce podporují dva druhy přiřazení: *přiřazení kopírování* a *přiřazení přesunutí*. V tomto článku "přiřazení" znamená přiřazení kopírování, pokud není výslovně uvedeno jinak. Informace o přiřazení přesunutí naleznete v tématu [Move konstruktors and Move Assignment OperatorsC++()](move-constructors-and-move-assignment-operators-cpp.md).
>
> Operace přiřazení a operace inicializace způsobí, že jsou objekty zkopírovány.

- **Přiřazení**: je-li hodnota jednoho objektu přiřazena jinému objektu, je první objekt zkopírován do druhého objektu. Proto:

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   způsobí, že je hodnota `b` zkopírována do `a`.

- **Inicializace**: inicializace probíhá při deklaraci nového objektu, pokud jsou argumenty předány funkcím podle hodnoty nebo když jsou hodnoty vráceny z funkcí podle hodnoty.

Pro objekty typu třídy lze definovat sémantiku „kopie“. Podívejte se například na tento kód:

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

Předcházející kód může znamenat „kopírovat obsah FILE1.DAT do FILE2.DAT“ nebo může znamenat „ignorovat FILE2.DAT a udělat z `b` druhý popisovač FILE1.DAT“. Následujícím způsobem je ke každé třídě třeba připojit odpovídající sémantiku kopírování.

- Pomocí **operátoru** přiřazení operátoru = spolu s odkazem na typ třídy jako návratový typ a parametr předaný odkazem **const** , například `ClassName& operator=(const ClassName& x);`.

- Pomocí konstruktoru kopie.

Pokud konstruktor Copy nedeklarujete, kompilátor pro vás vygeneruje konstruktor kopírovacího členu.  Pokud nedeklarujete operátor přiřazení kopie, kompilátor pro vás vygeneruje operátor přiřazení kopie s dalšími členy. Deklarování konstruktoru kopie nepotlačuje operátor přiřazení kopie vygenerovaný kompilátorem a opačně. Je-li jeden implementován, je doporučeno implementovat také druhý, aby byl význam kódu jasný.

Kopírovací konstruktor přebírá argument typu <em>class-name</em> <strong>&</strong>, kde *název třídy* je název třídy, pro kterou je konstruktor definovaný. Příklad:

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> Pokud je to možné, vytvořte typ argumentu **const const** <em>název třídy</em> <strong>&</strong> . To zabrání konstruktoru kopie v nechtěných úpravách objektu, ze kterého kopíruje. Umožňuje také kopírování z objektů **const** .

## <a name="compiler-generated-copy-constructors"></a>Konstruktory pro kopírování generované kompilátorem

Konstruktory pro kopírování generované kompilátorem, jako jsou uživatelsky definované konstruktory, mají jeden argument typu "odkaz na *název třídy*". Výjimkou je, že všechny základní třídy a třídy členů mají kopírovací konstruktory deklarované jako přebírání jednoho argumentu typu **const** <strong>&</strong> <em>název třídy</em> . V takovém případě je argument kopírovacího konstruktoru generovaný kompilátorem také **const**.

Když typ argumentu kopírovacího konstruktoru není **const**, inicializace zkopírováním objektu **const** vygeneruje chybu. Reverzní není true: Pokud je argument **const**, můžete inicializovat zkopírováním objektu, který není **const**.

Operátory přiřazení generované kompilátorem dodržují stejný vzor s ohledem na **const.** Přebírají jeden argument typu <em>class-name</em> <strong>&</strong> , pokud operátory přiřazení ve všech základních a členských třídách přebírají argumenty typu **const** <em>Class-Name</em> <strong>&</strong>. V tomto případě operátor přiřazení generované třídy přijímá argument **const** .

> [!NOTE]
> Pokud jsou virtuální základní třídy inicializovány kopírovacími konstruktory, ať už vygenerovanými kompilátorem nebo definovanými uživatelem, jsou inicializovány pouze jednou v místě, kde jsou vytvořeny.

Důsledky jsou podobné jako u těch, které jsou vygenerovány kopírovacím konstruktorem. Pokud typ argumentu není **const**, přiřazení z objektu **const** vygeneruje chybu. Opak není true: Pokud je **konstantní** hodnota přiřazena k hodnotě, která není **const**, přiřazení je úspěšné.

Další informace o přetížených operátorech přiřazení naleznete v tématu [přiřazení](../cpp/assignment.md).
