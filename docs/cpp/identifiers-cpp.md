---
title: Identifikátory (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d112e7ca192e56ede21d06e7ff17a775d661d01
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405227"
---
# <a name="identifiers-c"></a>Identifikátory (C++)
Identifikátor je sekvence znaků používaná k označení jednoho z následujících akcí:  
  
-   Název objektu nebo proměnné  
  
-   Třída, struktura nebo sjednocení název  
  
-   Název výčtového typu  
  
-   Člen třídy, struktury, unie nebo výčtu  
  
-   Funkce nebo funkce člena třídy  
  
-   Název TypeDef  
  
-   Název popisku  
  
-   Název – makro  
  
-   Parametr – makro  
  
 Následující znaky jsou povoleny jako libovolný znak identifikátoru:  
  
```  
_ a b c d e f g h i j k l m  
n o p q r s t u v w x y z  
A B C D E F G H I J K L M  
N O P Q R S T U V W X Y Z  
```  
  
 Určitých rozsahů univerzální názvy znaků jsou také v identifikátoru povolený.  Univerzální název znaku v identifikátoru nelze určit řídicí znak nebo znak v základní zdrojové znakové sady. Další informace najdete v tématu [znakových sad](../cpp/character-sets.md). Číslo rozsahy tyto Unicode kódu bodu jsou povolené jako univerzální názvy znaků pro libovolný znak v identifikátoru:  
  
-   00A8 00AA, 00AD, 00AF, 00B2 00B5, 00B7 00BA, 00BC 00BE, 00C 0-00 D 6, 8-00F6 00D, 00F8 00FF, 02FF 0100, 0370 167F, 1681 180D, 180F 1DBF, 1E00 1FFF, 200B 200D, 202A 202E, 2040 203F, 2054 206F 2060, 20CF 2070, 2100-218F, 2460-24FF, 2776-2793 2C: 00-2DFF, 2E80 2FFF, 3004 3007, 3021 302F, 3031 303F, 3040-D7FF F900 FD3D, FD40 FDCF, FDF0 FE1F, FE30 FE44, FE47-FFFD 10000-1FFFD, 20000 2FFFD, 30000 3FFFD, 40000 4FFFD, 50000 5FFFD, 60000 6FFFD, 70000 7FFFD, COŽ ODPOVÍDÁ 80 000 8FFFD, 9FFFD 90000, A0000 AFFFD, BFFFD B0000, C0000-CFFFD D0000-DFFFD E0000 EFFFD  
  
 Následující znaky jsou povoleny jako libovolný znak identifikátoru s výjimkou prvního:  
  
```  
0 1 2 3 4 5 6 7 8 9  
```  
  
 Číslo rozsahy tyto Unicode kódu bodu jsou povolené také jako univerzální názvy znaků pro libovolný znak identifikátoru s výjimkou prvního:  
  
-   0300-036F 1DC0 1DFF, 20D 0-20FF FE20 FE2F  
  
 **Specifické pro Microsoft**  
  
 Významných je pouze prvních 2 048 znaků identifikátorů Microsoft C++. Názvy pro uživatelem definované typy jsou "dekorovaných" kompilátorem za účelem zachování informací o typu. Výsledný název, včetně informací o typu, nemůže být delší než 2 048 znaků. (Viz [dekorované názvy](../build/reference/decorated-names.md) Další informace.) Mezi faktory ovlivňující délku dekorovaného identifikátoru jsou:  
  
-   Když identifikátor označuje objekt uživatelem definovaného typu nebo typ odvozený od uživatelem definovaného typu.  
  
-   Když identifikátor označuje funkci nebo typ odvozený z funkce.  
  
-   Počet argumentů funkce.  
  
 Znak dolaru `$` je znak platný identifikátor v jazyce Visual C++. Visual C++ můžete také použít skutečné znaky reprezentována povolených rozsahů univerzální názvy znaků v identifikátory. Tyto znaky Pokud chcete použít, musíte uložit soubor s použitím souboru kódování znakové stránky, která je obsahuje.  Tento příklad ukazuje, jak oba znaky s diakritikou a univerzální názvy znaků zaměnitelné ve vašem kódu.  
  
```cpp  
// extended_identifier.cpp  
// In Visual Studio, use File, Advanced Save Options to set  
// the file encoding to Unicode codepage 1200  
struct テスト         // Japanese 'test'  
{  
    void トスト() {}  // Japanese 'toast'  
};  
  
int main() {  
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form  
    パン.トスト();        // compiler recognizes UCN or literal form  
}  
```  
  
 Rozsah znaků v identifikátoru povolený je méně omezující při kompilaci C + +/ CLI kódu. Identifikátory v kódu zkompilovaném pomocí/CLR by měly dodržovat [Standard ECMA-335: Common Language infrastruktury (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 **Specifické pro END Microsoft**  
  
 První znak identifikátoru musí být abecední znak, velká nebo malá písmena, nebo podtržítko ( **_** ). Protože identifikátory jazyka C++ jsou malá a velká písmena, `fileName` se liší od `FileName`.  
  
 Identifikátory nesmí mít přesně stejný tvar a pád jako klíčová slova. Identifikátory, které obsahují klíčová slova jsou platné. Například `Pint` je platný identifikátor, přestože obsahuje **int**, což je klíčové slovo.  
  
 Použití dvou po sobě jdoucích podtržítek ( **__** ) na začátku identifikátoru nebo jedno vedoucí podtržítko následované jedním velkým písmenem je vyhrazeno pro implementace jazyka C++ ve všech oborech. Můžete Vyhněte se použití jednoho vedoucí znaku podtržítka následovaného malým písmenem pro názvy s rozsahem souboru z důvodu možných konfliktů současných nebo budoucích vyhrazených identifikátorů.  
  
## <a name="see-also"></a>Viz také:  
 [Lexikální konvence](../cpp/lexical-conventions.md)