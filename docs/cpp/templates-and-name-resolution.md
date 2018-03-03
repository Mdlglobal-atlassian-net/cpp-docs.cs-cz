---
title: "Rozlišení šablon a názvů | Microsoft Docs"
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
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cb6708a8b7631551a6e245c0777bcc6c9fb1a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="templates-and-name-resolution"></a>Rozlišení šablon a názvů

V definicích šablon existují tři typy názvů.  
  
-   Místně deklarované názvy, včetně názvu samotné šablony, a všechny názvy deklarované uvnitř definice šablony.  
  
-   Názvy z nadřazeného oboru mimo definici šablony.  
  
-   Názvy, které nějakým způsobem závisí na argumentech šablony, uváděné jako závislé názvy.  
  
 Zatímco první dva názvy se týkají také oborů třídy a funkce, jsou vyžadována zvláštní pravidla pro překlad názvů v definicích šablon pro řešení přidané složitosti závislých názvů. Je to proto, že kompilátor ví málo o těchto názvech, dokud není šablona vytvořena, protože by mohlo jít o zcela různé typy podle toho, se kterými argumenty šablony jsou použity. Nezávislé názvy jsou vyhledány podle obvyklých pravidel a v bodě definice šablony. Tyto názvy nezávislé na argumentech šablony jsou vyhledány jednou pro všechny specializace šablony. Závislé názvy nejsou vyhledány, dokud šablona není vytvořena, a jsou vyhledány odděleně pro každou specializaci.  
  
 Typ je závislý, pokud závisí na argumentech šablony. Konkrétně je typ závislý, je-li:  
  
-   Samotný argument šablony:  
  
    ```cpp
    T  
    ```  
  
-   Kvalifikovaný název s kvalifikací včetně závislého typu:  
  
    ```cpp
    T::myType  
    ```  
  
-   Kvalifikovaný název, pokud nekvalifikovaná část identifikuje závislý typ:  
  
    ```cpp
    N::T  
    ```  
  
-   Typ deklarovaný jako const nebo volatile, jehož základní typ je závislý typ:  
  
    ```cpp
    const T  
    ```  
  
-   Typ ukazatele, odkazu, pole nebo ukazatele na funkci na základě závislého typu:  
  
    ```cpp
    T *, T &, T [10], T (*)()  
    ```  
  
-   Pole, jehož velikost je založena na parametru šablony:  
  
    ```cpp
    template <int arg> class X {  
    int x[arg] ; // dependent type  
    }  
    ```  
  
-   Typ šablony vytvořený z parametru šablony:  
  
    ```cpp
    T<int>, MyTemplate<T>  
    ```  
  
## <a name="type-dependence-and-value-dependence"></a>Závislost na typu a závislost na hodnotě

 Názvy a výrazy, které jsou závislé na parametru šablony, se dělí na závislost na typu nebo závislost na hodnotě podle toho, zda je parametr šablony parametr typu nebo parametr hodnoty. Také všechny identifikátory deklarované v šabloně se závislostí typu na argumentu šablony jsou považovány za závislé na hodnotě, jako je celočíselný nebo výčtový typ inicializovaný s výrazem závislým na hodnotě.  
  
 Výrazy závislosti na typu nebo závislosti na hodnotě jsou výrazy zahrnující proměnné, které jsou závislé na typu nebo závislé na hodnotě. Tyto výrazy mohou mít sémantiku, která se liší v závislosti na parametrech použitých v šabloně.  
  
## <a name="see-also"></a>Viz také

 [Šablony](../cpp/templates-cpp.md)
