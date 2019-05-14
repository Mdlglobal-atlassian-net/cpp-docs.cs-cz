---
title: Organizace zdrojového kódu (šablony C++)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 1933758e47f2fcc0b63f0d16809591b932501854
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611390"
---
# <a name="source-code-organization-c-templates"></a>Organizace zdrojového kódu (šablony C++)

Při definování šablony třídy, musí organizovat zdrojový kód tak, že definice členů jsou viditelné pro kompilátor, když je nutné je.   Máte na výběr mezi používáním *zahrnutí modelu* nebo *explicitní vytváření instancí* modelu. V zařazení modelu zahrnete definice členů do každého souboru, který používá šablonu. Tento přístup je nejjednodušší a poskytuje maximální flexibilitu z hlediska konkrétní typy lze použít s vaší šablony. Jeho nevýhodou je, že můžete zvýšit dobu kompilace. Může být důležité, pokud projekt dopad a/nebo jsou velké zahrnuté soubory sami. S tímto přístupem explicitní vytváření instancí samotné šablony vytvoří instance konkrétní třídy nebo členy třídy pro konkrétní typy.  Tento přístup může zrychlit dobu kompilace, ale omezuje využití a pouze třídy, které šablony implementátora povolila předem. Obecně platí doporučujeme vám použít model zařazení, pokud časy kompilace stane problém.

## <a name="background"></a>Pozadí

Šablony nejsou stejně jako běžné třídy v tom smyslu, že kompilátor negeneruje objektový kód pro šablony nebo kterýkoli z jejích členů. Není nutné nic generovat dokud šablona není vytvořena s konkrétní typy. Když kompilátor narazí vytváření instancí šablon, jako `MyClass<int> mc;` a žádná třída s podpisu ještě neexistuje, vytvoří novou třídu. Pokusí se také pro generování kódu pro všechny členské funkce, které se používají. Pokud jsou tyto definice v souboru, který není #included, přímo nebo nepřímo, soubor .cpp, který je kompilován, kompilátor nemůže zobrazit.  Z kompilátoru tato akce není nutně chybu protože funkce může být definován v jiné jednotce překladu, ve kterém bude případ linker je najít.  Pokud linker nenajde, že kód, vyvolá **nevyřešené externí** chyby.

## <a name="the-inclusion-model"></a>Zahrnutí modelu

Nejběžnější a nejjednodušší způsob, jak zviditelnit definice šablon v celé jednotky převodu, je umístění definice v samotném souboru záhlaví.  Libovolný soubor .cpp, který používá šablonu jednoduše musí #include záhlaví. Toto je metoda použitá ve standardní knihovně.

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

S tímto přístupem kompilátor má přístup k definici úplnou šablonu a lze vytvořit instanci šablony na žádost pro libovolného typu. Je to jednoduché a je poměrně snadné ho spravovat. Model zahrnutí však mají svou cenu z hlediska časy kompilace.   Tyto náklady můžou být významné v velkých programech, zejména v případě záhlaví šablony #includes jiné záhlaví. Každý .cpp soubor, který #includes záhlaví získá vlastní kopii šablony funkce a všech definic. Linker obecně budou moci seřadí věci tak, že není skončit s více definic pro funkci, ale může zabrat určitý čas provést tuto práci. Programy menší čas navíc kompilace je pravděpodobně není důležité.

## <a name="the-explicit-instantiation-model"></a>Explicitní vytváření instancí modelu

Pokud model zařazení není vhodným pro váš projekt a konečně víte sadu typů, které se použije k vytvoření instance šablony, můžete oddělit kód šablony do souboru .h a .cpp a v souboru .cpp explicitně vytvořit instanci šablony. To způsobí vygenerování objektový kód, které kompilátor uvidí, když zjistí uživatele instancí.

Explicitní vytváření instancí vytvoříte pomocí šablony – klíčové slovo, za nímž následuje podpis metody, kterou chcete vytvořit instanci entity. To může být typ nebo člen. Pokud explicitně vytvořit instanci typu, jsou všechny členy instance.

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

V předchozím příkladu jsou i explicitní vytváření instancí v dolní části souboru .cpp. A `MyArray` slouží pouze pro **double** nebo `String` typy.

> [!NOTE]
> V C ++ 11 **exportovat** – klíčové slovo se přestala nabízet v rámci definice šablony. V praxi má malý vliv, protože většina kompilátorů nikdy podporována.