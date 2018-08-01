---
title: Deklarace a definice (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 895a2e3a78c425511f978454d07cf9574f7d8337
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403716"
---
# <a name="declarations-and-definitions-c"></a>Deklarace a definice (C++)
Deklarace zavádějí názvy v programu, například názvy proměnných, obory názvů, třídy a funkce. Deklarace také zadat informace o typu, jakož i další vlastnosti objektu, který je byl deklarován. Název musí být deklarován před jeho použitím; v jazyce C++ bod, ve kterém je název deklarován Určuje, zda je viditelný pro kompilátor. Nelze se odkazovat na funkci nebo třídu, která je deklarována někdy později v jednotce kompilace; můžete použít *předat dál deklarace* jsme toto omezení.  
  
 Definice určit, jaký kód nebo data název popisuje. Aby bylo možné přidělit prostor úložiště pro věc, která je deklarována jako vyžaduje kompilátor definici.  
  
## <a name="declarations"></a>Deklarace  
 Deklarace jednoho nebo více názvů zavádí do programu. Deklarace může v jednom programu vyskytují víc než jednou. Proto tříd, struktur, výčtu typů a dalších uživatelem definované typy mohou být deklarovány pro každou jednotku kompilace. Omezení u této deklarace více je, že všechny deklarace musí být identické. Deklarace také slouží jako definice, kromě případů, kdy deklarace:  
  
1.  Je prototyp funkce (deklarace funkce s žádná tělo funkce).  
  
2.  Obsahuje **extern** specifikátor, ale žádný inicializátor (objekty a proměnné) nebo tělo funkce (funkce). Znamená to, že definice není nutně v aktuální překladové jednotce a poskytuje název vnější propojení.  
  
3.  Je statický datový člen uvnitř deklarace třídy.  
  
     Protože statické datové členy třídy jsou proměnné diskrétního sdílet všechny objekty třídy, musí být definována a inicializována mimo deklaraci třídy. (Další informace o třídách a členy třídy, naleznete v tématu [třídy](../cpp/classes-and-structs-cpp.md).)  
  
4.  Je název deklarace třídy s žádná následující definice například `class T;`.  
  
5.  Je **typedef** příkazu.  
  
 Příkladem deklarace, které jsou také definice jsou:  
  
```cpp 
// Declare and define int variables i and j.  
int i;  
int j = 10;  
  
// Declare enumeration suits.  
enum suits { Spades = 1, Clubs, Hearts, Diamonds };  
  
// Declare class CheckBox.  
class CheckBox : public Control  
{  
public:  
            Boolean IsChecked();  
    virtual int     ChangeState() = 0;  
};  
```  
  
 Některé deklarace, které nejsou definicemi jsou:  
  
```cpp 
extern int i;  
char *strchr( const char *Str, const char Target );  
```  
  
 Název se považuje za deklarovat ihned po jeho deklarátor, ale před jeho vlastním inicializátoru (volitelné). Další informace najdete v tématu [bod deklarace](../cpp/point-of-declaration-in-cpp.md).  
  
 Probíhá deklarace *oboru*. Obor určuje, zda se název deklarován a dobu trvání objekt definovaný, případné. Další informace o interakci pravidla rozsahu s deklaracemi, naleznete v tématu [oboru](../cpp/scope-visual-cpp.md).  
  
 Deklarace objektu je také definice neobsahuje **extern** – specifikátor třídy úložiště popsané v [třídy úložiště](storage-classes-cpp.md). Deklarace funkce je také definice, pokud je prototyp. Prototyp se hlavička funkce bez definování těla funkce. Definice objektu způsobí, že přidělení úložiště a odpovídající inicializace pro daný objekt.  
  
## <a name="definitions"></a>Definice  
 Definice je jedinečný specifikace objektu nebo proměnné, funkce, třídy nebo výčtu. Vzhledem k tomu, že definice musí být jedinečný, program může obsahovat jenom jednu definici pro danou aplikaci prvku. Může existovat vztahu mnoha k jednomu jinému mezi deklarace a definice. Existují dva případy, ve kterých prvek programu deklarovány a není definována:  
  
1.  Funkce je deklarovaná, ale nikdy odkazována pomocí volání funkce nebo výraz přebírající adresu funkce.  
  
2.  Třída se používá pouze způsobem, který nevyžaduje znát jeho definici. Třídy však musí být deklarována. Následující kód znázorňuje takový případ:  
  
    ```cpp 
    // definitions.cpp  
    class WindowCounter;   // Forward declaration; no definition  
  
    class Window  
    {  
       // Definition of WindowCounter not required  
       static WindowCounter windowCounter;  
    };  
  
    int main()  
    {  
    }  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [Základní koncepty](../cpp/basic-concepts-cpp.md)   
 [Bod deklarace](../cpp/point-of-declaration-in-cpp.md)