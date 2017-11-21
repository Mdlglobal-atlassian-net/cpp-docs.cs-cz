---
title: "Konstruktory a operátory přiřazení pro kopírování (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b84bb6f0558b58bd83819fbef7e8e9e9c392bd94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Konstruktory a operátory přiřazení pro kopírování (C++)
> [!NOTE]
>  Počínaje C ++ 11, dva druhy přiřazení jsou podporovány v jazyce: *zkopírujte přiřazení* a *přesunout přiřazení*. V tomto článku "přiřazení" znamená kopie přiřazení, pokud není výslovně uvedeno jinak. Informace o přiřazení přesunutí najdete v tématu [přesunout konstruktory a operátory přesunout přiřazení (C++)](http://msdn.microsoft.com/en-us/1442de5f-37a5-42a1-83a6-ec9cfe0414db).  
>   
>  Operace přiřazení a operace inicializace způsobí, že jsou objekty zkopírovány.  
  
-   **Přiřazení**: když hodnota jednoho objektu je přiřazen k jinému objektu, první objekt se zkopírují na druhý objekt. Proto  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     způsobí, že je hodnota `b` zkopírována do `a`.  
  
-   **Inicializace**: Inicializace dojde, když je deklarován nový objekt, když jsou předána argumenty funkce hodnotou, nebo když hodnoty jsou vráceny z funkcí podle hodnoty.  
  
 Pro objekty typu třídy lze definovat sémantiku „kopie“. Podívejte se například na tento kód:  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 Předcházející kód může znamenat „kopírovat obsah FILE1.DAT do FILE2.DAT“ nebo může znamenat „ignorovat FILE2.DAT a udělat z `b` druhý popisovač FILE1.DAT“. Následujícím způsobem je ke každé třídě třeba připojit odpovídající sémantiku kopírování.  
  
-   Pomocí operátoru přiřazení `operator=` spolu s odkazem na typ třídy jako návratový typ a parametrem předaným pomocí odkazu `const` – například `ClassName& operator=(const ClassName& x);`.  
  
-   Pomocí konstruktoru kopie.   
  
 Pokud neprovedete deklaraci kopírovacího konstruktoru, kompilátor vygeneruje member-wise kopírovacího konstruktoru za vás.  Pokud neprovedete deklaraci operátor přiřazení kopírování, kompilátor generuje operátor přiřazení member-wise kopie za vás. Deklarování konstruktoru kopie nepotlačuje operátor přiřazení kopie vygenerovaný kompilátorem a opačně. Je-li jeden implementován, je doporučeno implementovat také druhý, aby byl význam kódu jasný.  
   
 Konstruktor copy používá argument typu *název třídy***&**, kde *název třídy* je název třídy, pro který je definován v konstruktoru. Příklad:  
  
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
>  Ujistěte se, typ argumentu konstruktor copy *const název třídy*  **&**  kdykoli je to možné. To zabrání konstruktoru kopie v nechtěných úpravách objektu, ze kterého kopíruje. Taky umožňuje kopírování z **const** objekty.  
  
## <a name="compiler-generated-copy-constructors"></a>Kopírovací konstruktory vygenerované kompilátoru  
 Kopírování generované kompilátorem konstruktory jako uživatelem definované kopie konstruktorů mít jeden argument typu "odkaz na *název třídy*." Výjimka je v případě všechny základní třídy a člen třídy kopie konstruktorů deklarován jako trvá jeden argument typu **const** *název třídy***&**. V takovém případě je argument konstruktoru kopírování generované kompilátorem také **const**.  
  
 Když je typ argumentu pro konstruktor copy není **const**, inicializace zkopírováním **const** objektu, vygeneruje se chyba. Naopak není pravda: Pokud je argumentem **const**, bude možné inicializovat zkopírováním objekt, který není **const**.  
  
 Operátory přiřazení generované kompilátorem postupují stejným způsobem s ohledem na **const.** Jejich trvat jeden argument typu *název třídy*  **&**  Pokud operátory přiřazení v všechny základní a člena třídy trvat argumenty typu **const** *název třídy &.* V takovém případě je třída generované trvá operátor přiřazení **const** argument.  
  
> [!NOTE]
>  Pokud jsou virtuální základní třídy inicializovány kopírovacími konstruktory, ať už vygenerovanými kompilátorem nebo definovanými uživatelem, jsou inicializovány pouze jednou v místě, kde jsou vytvořeny.  
  
 Důsledky jsou podobné jako u těch, které jsou vygenerovány kopírovacím konstruktorem. Pokud není typ argumentu je **const**, přiřazení z **const** objektu, vygeneruje se chyba. Naopak není pravda: Pokud **const** hodnota je přiřazena hodnotu, která není **const**, úspěšné přiřazení.  
  
 Další informace o přiřazení přetížené operátory najdete v tématu [přiřazení](../cpp/assignment.md).  
  
