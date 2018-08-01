---
title: Konstruktory a operátory přiřazení pro kopírování (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24f9e4e5b3d157f23c18d46f2857b29e6960e82e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405753"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Konstruktory a operátory přiřazení pro kopírování (C++)
> [!NOTE]
>  Od verze C ++ 11, dva druhy přiřazení jsou podporovány v jazyce: *zkopírujte přiřazení* a *přesunutí přiřazení*. V tomto článku "přiřazení" znamená přiřazení kopie, pokud není výslovně uvedeno jinak. Informace o přiřazení pro přesun najdete v tématu [konstruktory přesunutí a operátory přiřazení přesunutí (C++)](http://msdn.microsoft.com/1442de5f-37a5-42a1-83a6-ec9cfe0414db).  
>   
>  Operace přiřazení a operace inicializace způsobí, že jsou objekty zkopírovány.  
  
-   **Přiřazení**: Pokud je hodnota jednoho objektu přiřazena jiném objektu, první objekt zkopírován do druhého objektu. Proto  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     způsobí, že je hodnota `b` zkopírována do `a`.  
  
-   **Inicializace**: inicializaci dochází při deklaraci nového objektu, kdy jsou argumenty předány funkcím podle hodnoty nebo hodnoty jsou vráceny ve funkcích podle hodnoty.  
  
 Pro objekty typu třídy lze definovat sémantiku „kopie“. Podívejte se například na tento kód:  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 Předcházející kód může znamenat „kopírovat obsah FILE1.DAT do FILE2.DAT“ nebo může znamenat „ignorovat FILE2.DAT a udělat z `b` druhý popisovač FILE1.DAT“. Následujícím způsobem je ke každé třídě třeba připojit odpovídající sémantiku kopírování.  
  
-   Pomocí operátoru přiřazení **operátoru =** spolu s odkazem na typ třídy jako návratový typ a parametrem předaným pomocí **const** odkaz – například `ClassName& operator=(const ClassName& x);`.  
  
-   Pomocí konstruktoru kopie.   
  
 Pokud není třeba deklarovat kopírovací konstruktor, kompilátor vygeneruje požadování kopírovacího konstruktoru pro vás.  Pokud není třeba deklarovat operátor přiřazení kopie, vygeneruje kompilátor požadování kopírovacího operátoru přiřazení pro vás. Deklarování konstruktoru kopie nepotlačuje operátor přiřazení kopie vygenerovaný kompilátorem a opačně. Je-li jeden implementován, je doporučeno implementovat také druhý, aby byl význam kódu jasný.  
   
 Konstruktor kopie přebírá argument typu * třídy – název ***&**, kde *název třídy* je název třídy, pro kterou je konstruktor definován. Příklad:  
  
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
>  Ujistěte se, typ argumentu kopírovacího konstruktoru *třídy const-název *** &** kdykoli je to možné. To zabrání konstruktoru kopie v nechtěných úpravách objektu, ze kterého kopíruje. Také umožněno kopírování z **const** objekty.  
  
## <a name="compiler-generated-copy-constructors"></a>Generovaný kompilátorem kopírovací konstruktory  
 Kompilátor kopírovací konstruktory vygenerované kompilátorem, jako je uživatelem definovaný kopírovací konstruktory, mají jediný argument typu "odkaz na *název třídy*." Výjimkou je, když všechny základní a členské třídy musí mít kopírovací konstruktory deklarované, aby přijímaly jediný argument typu **const** * třídy – název ***&**. V takovém případě je argument kopírovacího konstruktoru vygenerovaný kompilátorem také **const**.  
  
 Pokud typ argumentu kopírovacího konstruktoru není **const**, inicializace kopírováním **const** vygeneruje chybu. Opak není pravdou: Pokud je argumentem **const**, můžete inicializovat zkopírováním objektu, který není **const**.  
  
 Operátory přiřazení vygenerované kompilátorem následují stejný vzor s ohledem na **const.** Přijímají jediný argument typu *třídy – název *** &** Pokud operátory přiřazení ve všech základních a členských třídách přijímají argumenty typu **const** *název třídy &.* V takovém případě vygenerovaný třídou přijímá operátor přiřazení **const** argument.  
  
> [!NOTE]
>  Pokud jsou virtuální základní třídy inicializovány kopírovacími konstruktory, ať už vygenerovanými kompilátorem nebo definovanými uživatelem, jsou inicializovány pouze jednou v místě, kde jsou vytvořeny.  
  
 Důsledky jsou podobné jako u těch, které jsou vygenerovány kopírovacím konstruktorem. Pokud typ argumentu není **const**, přiřazení **const** vygeneruje chybu. Opak není pravdou: Pokud **const** hodnotu, která není přiřazena hodnota **const**, přiřazení uspěje.  
  
 Další informace o přetížených operátorech přiřazení naleznete v tématu [přiřazení](../cpp/assignment.md).  