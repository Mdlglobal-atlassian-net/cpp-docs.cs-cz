---
title: struktury (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 4f4b343097be6c15b5a273fd4e2a59198858d576
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947511"
---
# <a name="struct-c"></a>struct (C++)
**Struktura** – klíčové slovo definuje typ struktury anebo proměnnou typu Struktura.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[template-spec] struct[ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### <a name="parameters"></a>Parametry  
 *specifikace šablony*  
 Volitelné specifikace šablony. Další informace najdete v [specifikace šablony](templates-cpp.md).  
  
 *struct*  
 **Struktura** – klíčové slovo.  
  
 *MS-decl-spec*  
 Volitelná specifikace paměťové třídy. Další informace najdete [__declspec](../cpp/declspec.md) – klíčové slovo.  
  
 *Značka*  
 Název typu daný pro strukturu. Značka se změní na vyhrazené slovo v rámci struktury. Značka je volitelná. Pokud je tento argument vynechán, je definována anonymní struktura. Další informace najdete v tématu [anonymní typy třídy](../cpp/anonymous-class-types.md).  
  
 *Base-list*  
 Volitelný seznam tříd nebo struktur, ze kterých tato struktura odvodí svoje členy. Zobrazit [základní třídy](../cpp/base-classes.md) Další informace. Každý název základní třídy nebo struktury může být uvozen specifikátorem přístupu ([veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md)) a [virtuální](../cpp/virtual-cpp.md) klíčové slovo. Viz tabulka pro přístup ke členu [řízení přístupu ke členům třídy](member-access-control-cpp.md) Další informace.  
  
 *seznam členů*  
 Seznam členů struktury. Odkazovat na [přehled členů třídy](../cpp/class-member-overview.md) Další informace. Jediný rozdíl zde je, že **struktura** je použito místo **třídy**.  
  
 *deklarátory*  
 Seznam deklarátoru určující názvy třídy. Seznam deklarátoru deklarující jednu nebo více instancí typu struktura. Deklarátory mohou obsahovat inicializační seznamy, pokud jsou všechny datové členy třídy **veřejné**. Inicializační seznamy jsou běžné ve strukturách, protože datoví členové mají **veřejné** ve výchozím nastavení.  Zobrazit [přehled Deklarátorů](../cpp/overview-of-declarators.md) Další informace.  
  
## <a name="remarks"></a>Poznámky  
 Typ struktury je složený typ definovaný uživatelem. Skládá se z polí nebo členů, které mohou mít různé typy.  
  
 V jazyce C++ je struktura je stejná jako třída s tím rozdílem, že její členy jsou **veřejné** ve výchozím nastavení.  
  
 Informace o spravovaných třídách a strukturách naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="using-a-structure"></a>Používání struktury  
 V jazyce C, je nutné explicitně zadat **struktura** – klíčové slovo pro deklaraci struktury. V jazyce C++, nepotřebujete k použití **struktura** – klíčové slovo po definování typu.  
  
 Proměnné můžete deklarovat, pokud je typ struktury definován umístěním jednoho nebo více názvů proměnných oddělených čárkami mezi uzavírací závorkou a středníkem.  
  
 Proměnné struktury je možné inicializovat. Inicializace pro každou proměnnou musí být uzavřena do složených závorek.  
  
 Související informace naleznete v tématu [třídy](../cpp/class-cpp.md), [sjednocení](../cpp/unions.md), a [výčtu](../cpp/enumerations-cpp.md).  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
