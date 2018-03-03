---
title: Deklarace a definice (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea0f8210993e494cbd4795a2c4cf7c6c0afa8aa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="declarations-and-definitions-c"></a>Deklarace a definice (C++)
Deklarace zavést názvy v programu, například názvy proměnných, obory názvů, třídy a funkce. Deklarace také určit typ informací, jakož i dalších vlastností objektu, který je právě deklarován. Název musí být deklarován před jeho použitím; v jazyce C++ bod, ve kterém je deklarovaná název určuje, zda je viditelná pro kompilátor. Nemůže odkazovat na funkci nebo třídu, která je deklarovaná novější někde v jednotce kompilace; můžete použít *předávat deklarace* získat obejít toto omezení.  
  
 Definice zadejte, jaký kód nebo data popisuje název. Aby bylo možné přidělit prostor úložiště pro věcí, kterou je právě deklarovaný vyžaduje kompilátor definici.  
  
## <a name="declarations"></a>Deklarace  
 Deklaraci představuje jeden nebo více názvů do programu. Deklarace můžete v programu vyskytnout více než jednou. Proto třídy, struktury, výčet typů a další uživatelem definované typy lze deklarovat pro každou jednotku kompilace. Omezení pro tuto deklaraci více je, že všechny deklarace, musí být identické. Deklarace taky sloužit jako definice, s výjimkou případů, kdy deklaraci:  
  
1.  Je funkce prototyp (deklaraci funkce s žádné tělo funkce).  
  
2.  Obsahuje `extern` specifikace, ale žádné inicializátoru (objekty a proměnné) nebo tělo funkce (funkce). To označuje, že definice není nutně aktuální jednotku překlad poskytuje název externí propojení.  
  
3.  Je členem statických dat uvnitř deklaraci třídy.  
  
     Vzhledem k tomu, že statická třída datových členů jsou proměnné diskrétní sdílí všechny objekty třídy, musí být definovaný a inicializovat mimo deklaraci třídy. (Další informace o třídy a jejich členové najdete v tématu [třídy](../cpp/classes-and-structs-cpp.md).)  
  
4.  Jako je název deklaraci třídy s žádné následující definice `class T;`.  
  
5.  Je `typedef` příkaz.  
  
 Příklady deklarace, které jsou také definice:  
  
```  
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
  
 Jsou některé deklarace, které nejsou definice:  
  
```  
  
extern int i;  
char *strchr( const char *Str, const char Target );  
```  
  
 Název se považuje deklarovat ihned po jeho deklarátor, ale před jeho inicializátoru (volitelné). Další informace najdete v tématu [deklarace bodu](../cpp/point-of-declaration-in-cpp.md).  
  
 Deklarace, ke kterým došlo v *oboru*. Obor Určuje viditelnost deklarovaný název a trvání objekt definovaný, pokud existuje. Další informace o interakci pravidla rozsahu s deklaracemi, najdete v tématu [oboru](../cpp/scope-visual-cpp.md).  
  
 Deklarace objektu je také definice pokud obsahuje `extern` – specifikátor třídy úložiště popsané v [třídy úložiště](storage-classes-cpp.md). Deklaraci funkce je také definice, pokud je prototypu. Prototyp je hlavičku funkce bez definující tělo funkce. Definici objektu způsobí, že přidělení úložiště a odpovídající inicializacích pro tento objekt.  
  
## <a name="definitions"></a>Definice  
 Definice je jedinečný specifikace objektu nebo proměnné, funkce, třída nebo enumerátor. Protože definice musí být jedinečný, program může obsahovat pouze jednu definici pro daný program element. Může být n 1 propojeni deklarace a definice. Existují dva případy, ve kterých můžete deklarovaný program element a není definován:  
  
1.  Funkce je deklarovaná, ale nikdy odkazuje volání funkce nebo s výraz, který přebírá adresu funkce.  
  
2.  Třída se používá pouze způsobem, který nevyžaduje být známé jeho definice. Třída, však musí být deklarován. Následující kód ukazuje takovém případě:  
  
    ```  
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
  
## <a name="see-also"></a>Viz také  
 [Základní koncepty](../cpp/basic-concepts-cpp.md)   
 [Bod deklarace](../cpp/point-of-declaration-in-cpp.md)