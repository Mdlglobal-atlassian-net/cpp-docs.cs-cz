---
title: Organizace zdrojového kódu (C++ šablony)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 76898d04e5f9f0576898eb40945b7718c650d71a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178727"
---
# <a name="source-code-organization-c-templates"></a>Organizace zdrojového kódu (C++ šablony)

Při definování šablony třídy je nutné organizovat zdrojový kód takovým způsobem, že definice členů jsou pro kompilátor viditelné, když je potřebuje.   Můžete zvolit použití *modelu zahrnutí* nebo *explicitního modelu vytváření instancí* . V modelu zahrnutí zahrnete definice členů do každého souboru, který používá šablonu. Tento přístup je nejjednodušší a poskytuje maximální flexibilitu z hlediska toho, jaké konkrétní typy lze s vaší šablonou použít. Nevýhodou je, že může prodloužit dobu kompilace. Dopad může být významný v případě, že projekt nebo samotné vložené soubory jsou velké. Pomocí explicitního přístupu k vytváření instancí vlastní šablona vytváří instance konkrétních tříd nebo členů třídy pro konkrétní typy.  Tento přístup může zrychlit dobu kompilace, ale omezuje využití jenom na ty třídy, které implementátora šablony povolil před časem. Obecně doporučujeme, abyste používali model zahrnutí, pokud se neobjeví Chyba kompilace.

## <a name="background"></a>Podrobnosti

Šablony nejsou jako běžné třídy v tom smyslu, že kompilátor negeneruje kód objektu pro šablonu nebo žádné z jejích členů. Není nic k vygenerování, dokud není vytvořena instance šablony se konkrétními typy. Když kompilátor narazí na instanci šablony, jako je `MyClass<int> mc;`, a zatím neexistuje žádná třída s tímto podpisem, vygeneruje novou třídu. Také se pokusí vygenerovat kód pro jakékoli členské funkce, které jsou použity. Pokud jsou tyto definice v souboru, který není #included, přímo nebo nepřímo, v souboru. cpp, který je kompilován, kompilátor je nemůže zobrazit.  Z pohledu kompilátoru není to nutně chyba, protože funkce mohou být definovány v jiné jednotce překladu, v takovém případě je linker nalezne.  Pokud linker tento kód nenajde, vyvolá **nevyřešenou externí** chybu.

## <a name="the-inclusion-model"></a>Model zahrnutí

Nejjednodušší a nejběžnější způsob, jak vytvořit definice šablon v rámci jednotky překladu, je umístit definice do samotného souboru hlaviček.  Libovolný soubor. cpp, který používá šablonu, má jednoduše #include hlavičce. Toto je přístup, který se používá ve standardní knihovně.

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

S tímto přístupem má kompilátor přístup k kompletní definici šablony a může vytvářet instance šablon na vyžádání pro libovolný typ. Údržba je jednoduchá a poměrně snadná. Model zahrnutí ale má za následek náklady na období kompilace.   Tyto náklady mohou být významné ve velkých programech, zejména pokud záhlaví samotné šablony #includes jiné hlavičky. Každý soubor. cpp, který #includes hlavičce, získá svoji vlastní kopii šablon funkcí a všech definic. Linker bude obecně schopný řadit objekty tak, že nekončí více definicí funkce, ale tato práce trvá déle. V menších programech, které ještě delší dobu kompilace pravděpodobně nejsou významné.

## <a name="the-explicit-instantiation-model"></a>Model explicitního vytváření instancí

Pokud model zahrnutí není pro váš projekt životaschopný a znáte konečně sadu typů, které budou použity k vytvoření instance šablony, můžete oddělit kód šablony do souboru. h a. cpp a v souboru. cpp explicitně vytvořit instanci šablon. Tím dojde k vygenerování kódu objektu, který bude kompilátor zobrazovat, když dojde k vytváření instancí uživatele.

Explicitní vytváření instancí vytvoříte pomocí šablony klíčového slova následovaný signaturou entity, kterou chcete vytvořit. Může to být typ nebo člen. Je-li explicitně vytvořena instance typu, jsou vytvořeny instance všech členů.

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

V předchozím příkladu jsou explicitní vytváření instancí na konci souboru. cpp. `MyArray` lze použít pouze pro typ **Double** nebo `String`.

> [!NOTE]
> V jazyce C++ 11 bylo klíčové slovo **Export** zastaralé v kontextu definic šablon. V praktických výrazech má tento malý dopad, protože většina kompilátorů ji nikdy nepodporuje.
