---
title: "Zdroj organizace kódu (C++ šablony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 1b3b17c17bad3834774f747548dda6710e178cb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="source-code-organization-c-templates"></a>Zdrojový kód organizace (šablonami C++)

Při definování šablona třídy, musí uspořádat zdrojový kód tak, že definice člen jsou viditelné pro kompilátor, když je potřebuje.   Máte možnost volby použití *zahrnutí modelu* nebo *explicitní vytvoření instance* modelu. V modelu zahrnutí zahrnují definice člen v každý soubor, který používá šablonu. Tento přístup je nejjednodušší a poskytuje maximální flexibilitu z hlediska, jaké konkrétní typy lze použít s vaší šablony. Její nevýhodou je, že se může prodloužit dobu kompilace. Dopad může být důležité, pokud projektu nebo jsou velké zahrnuté soubory sami. S tímto přístupem explicitní vytvoření instance samotné šablony vytvoří konkrétní třídy nebo členy třídy pro konkrétní typy.  Tento postup můžete urychlit dobu kompilace, ale omezuje využití pouze na třídy, které šablony implementátor povolil předem. Obecně platí doporučujeme použít model zahrnutí, nejsou-li dobu kompilace k potížím.  
  
## <a name="background"></a>Pozadí

 Šablony nejsou stejně jako obyčejnou třídy v tom smyslu, že kompilátor nevygeneruje žádný kód objektu pro šablonu, nebo kterýkoli z jejích členů. Není co ke generování dokud s konkrétní typy vytvoření instance šablony. Když kompilátor narazí vytváření instancí šablon, jako `MyClass<int> mc;` a neexistuje žádná třída této podpisem existuje ještě, vygeneruje nové třídy. Taky automatický pokus o generování kódu pro všechny členské funkce, které se používají. Pokud jsou tyto definice v souboru, který není #included, přímo ani nepřímo, sada soubor, který se bude kompilovat, kompilátor neuvidí.  Z kompilátoru tato akce není nutně chybu protože funkce může být definována v jiné jednotce překlad, ve kterém bude případ linkeru je vyhledat.  Pokud linkeru nenajde tento kód, vyvolá **nerozpoznané externí** chyby.  

## <a name="the-inclusion-model"></a>Zahrnutí modelu

 Nejjednodušší a nejběžnější způsob zobrazována prostřednictvím překlad jednotky, aby definice šablony je uvést definice v samotném souboru záhlaví.  Všech sada souborů, které používá šablonu jednoduše musí #include záhlaví. Jedná se o postup používá standardní knihovny.  
  
```cpp
#ifndef MYARRAY  
#define MYARRAY  
#include <iostream>  
  
template<typename T, size_t N>  
class MyArray  
{  
    T arr[N];  
public:  
    // Full definitions:  
    MyArray(){}  
    void Print()  
    {  
        for (const auto v : arr)  
        {  
            std::cout << v << " , ";  
        }  
    }  
  
    T& operator[](int i)  
   {  
       return arr[i];  
   }   
};  
#endif  
```  
  
 S tímto přístupem kompilátor má přístup k definici úplnou šablonu a může vytvořit instanci šablony na žádost pro libovolného typu. Je jednoduchý a udržovat je poměrně snadné. Zahrnutí modelu však nemá náklady z hlediska dobu kompilace.   Tyto poplatky může být důležité v programech, velké, zvlášť pokud záhlaví šablony #includes jiné záhlaví. Každý sada souboru, který #includes hlavičku získají vlastní kopii šablony funkce a všech definic. Linkeru obecně budou moci vyřešit věcí, aby nebyla výsledná několik definic pro funkci, ale trvá dobu tuto práci. V menší programy čas navíc kompilace je pravděpodobně není důležité.  
  
## <a name="the-explicit-instantiation-model"></a>Explicitní vytvoření instance modelu

 Pokud model zahrnutí není vhodným pro svůj projekt a konečně znáte sadu typů, které se použijí k vytvoření instance šablony, můžete oddělit kód šablony do souboru sada a v souboru explicitně vytvořit instanci šablony. To způsobí kód objektu má být vygenerován které kompilátor uvidí, když zjistí konkretizací uživatele.  
  
 Explicitní vytvoření instance vytvoříte pomocí šablony – klíčové slovo, za nímž následuje podpis entity, které chcete vytvořit instanci. To může být typ nebo člen. Pokud explicitně vytvořit instanci typu, všichni členové instance.  
  
```cpp
template MyArray<double, 5>;  
```  
  
```cpp
//MyArray.h  
#ifndef MYARRAY  
#define MYARRAY  
  
template<typename T, size_t N>  
class MyArray  
{  
    T arr[N];  
public:  
    MyArray();  
    void Print();  
    T& operator[](int i);  
};  
#endif  
  
//MyArray.cpp  
#include "stdafx.h"  
#include <iostream>  
#include "MyArray.h"  
  
using namespace std;  
  
template<typename T, size_t N>  
MyArray<T,N>::MyArray(){}  
  
template<typename T, size_t N>  
void MyArray<T,N>::Print()  
{  
    for(const auto v : arr)  
    {  
        cout << v << "'";  
    }  
    cout << endl;  
}  
  
template MyArray<double, 5>;template MyArray<string, 5>;  
```  
  
 V předchozím příkladu jsou explicitní konkretizací na konci souboru. A `MyArray` mohou být použity pouze pro **dvojité** nebo **řetězec** typy.  
  
> [!NOTE]
>  V C ++ 11 **exportovat** – klíčové slovo se považovat za zastaralou v kontextu definice šablony. V praxi má malý vliv, protože většina kompilátory nikdy podporována.
