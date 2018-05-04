---
title: struct (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- struct_cpp
dev_langs:
- C++
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9ea6bea20ad1591db9b07507b4db959d10a318
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="struct-c"></a>struct (C++)
`struct` – Klíčové slovo definuje typ struktury nebo proměnná typ struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[template-spec] struct[ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### <a name="parameters"></a>Parametry  
 `template-spec`  
 Volitelné specifikace šablony. Další informace najdete v části [specifikace šablony](templates-cpp.md).  
  
 `struct`  
 `struct` – Klíčové slovo.  
  
 `ms-decl-spec`  
 Volitelná specifikace paměťové třídy. Další informace najdete v části [__declspec](../cpp/declspec.md) – klíčové slovo.  
  
 `tag`  
 Název typu daný pro strukturu. Značka se změní na vyhrazené slovo v rámci struktury. Značka je volitelná. Pokud je tento argument vynechán, je definována anonymní struktura. Další informace najdete v tématu [anonymní typy třídy](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 Volitelný seznam tříd nebo struktur, ze kterých tato struktura odvodí svoje členy. V tématu [základní třídy](../cpp/base-classes.md) Další informace. Každý název základní třídu nebo strukturu lze předcházet specifikátor přístupu ([veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md)) a [virtuální](../cpp/virtual-cpp.md) – klíčové slovo. Podívejte se na tabulku přístup ke členu v [řízení přístupu ke členům třídy](member-access-control-cpp.md) Další informace.  
  
 `member-list`  
 Seznam členů struktury. Odkazovat na [přehled členů třídy](../cpp/class-member-overview.md) Další informace. Jediným rozdílem je, že `struct` slouží místě `class`.  
  
 `declarators`  
 Seznam deklarátoru určující názvy třídy. Seznam deklarátoru deklarující jednu nebo více instancí typu struktura. Deklarátory můžou obsahovat inicializační seznamy, pokud jsou všechny datové členy třídy `public`. Inicializační seznamy jsou běžné při struktury, protože jsou datové členy `public` ve výchozím nastavení.  V tématu [přehled Deklarátory](../cpp/overview-of-declarators.md) Další informace.  
  
## <a name="remarks"></a>Poznámky  
 Typ struktury je složený typ definovaný uživatelem. Skládá se z polí nebo členů, které mohou mít různé typy.  
  
 V jazyce C++ struktura je stejná jako třída s tím rozdílem, že jeho členové jsou `public` ve výchozím nastavení.  
  
 Informace na spravované třídy a struktury najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="using-a-structure"></a>Používání struktury  
 V jazyce C, je nutné explicitně zadat `struct` – klíčové slovo do definice struktury. V jazyce C++, není nutné používat `struct` – klíčové slovo po definování typu.  
  
 Proměnné můžete deklarovat, pokud je typ struktury definován umístěním jednoho nebo více názvů proměnných oddělených čárkami mezi uzavírací závorkou a středníkem.  
  
 Proměnné struktury je možné inicializovat. Inicializace pro každou proměnnou musí být uzavřena do složených závorek.  
  
 Související informace najdete v tématu [třída](../cpp/class-cpp.md), [sjednocení](../cpp/unions.md), a [výčtu](../cpp/enumerations-cpp.md).  
  
## <a name="example"></a>Příklad  
  
```  
#include <iostream>  
using namespace std;  
  
struct PERSON {   // Declare PERSON struct type  
    int age;   // Declare member types  
    long ss;  
    float weight;  
    char name[25];  
} family_member;   // Define object of type PERSON  
  
struct CELL {   // Declare CELL bit field  
    unsigned short character  : 8;  // 00000000 ????????  
    unsigned short foreground : 3;  // 00000??? 00000000  
    unsigned short intensity  : 1;  // 0000?000 00000000  
    unsigned short background : 3;  // 0???0000 00000000  
    unsigned short blink      : 1;  // ?0000000 00000000  
} screen[25][80];       // Array of bit fields   
  
int main() {  
    struct PERSON sister;   // C style structure declaration  
    PERSON brother;   // C++ style structure declaration  
    sister.age = 13;   // assign values to members  
    brother.age = 7;  
    cout << "sister.age = " << sister.age << '\n';  
    cout << "brother.age = " << brother.age << '\n';  
  
    CELL my_cell;  
    my_cell.character = 1;  
    cout << "my_cell.character = " << my_cell.character;  
}  
// Output:  
// sister.age = 13  
// brother.age = 7  
// my_cell.character = 1  
```  
  
