---
title: Identifikátory (C++) | Microsoft Docs
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
ms.openlocfilehash: 8bb25713ad4f4a8ab1821eac4f7bf05d671bb101
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="identifiers-c"></a>Identifikátory (C++)
Identifikátor se používá k označení jednu z následujících znaků:  
  
-   Název objektu nebo proměnná  
  
-   Třída, struktura nebo union název  
  
-   Název výčtového typu  
  
-   Členy třídy, struktury, sjednocení nebo – výčet  
  
-   Funkce nebo funkce člena třídy  
  
-   Název definice TypeDef  
  
-   Název popisku  
  
-   Název makra  
  
-   Parametr – makro  
  
 Jako libovolný znak identifikátoru jsou povoleny následující znaky:  
  
```  
_ a b c d e f g h i j k l m  
n o p q r s t u v w x y z  
A B C D E F G H I J K L M  
N O P Q R S T U V W X Y Z  
```  
  
 V identifikátoru jsou také povolené určitých rozsahů univerzální názvy znaků.  Název universal znak v identifikátoru nelze určit řídicí znak nebo znak ve znakové sadě základní zdroj. Další informace najdete v tématu [znakových sad](../cpp/character-sets.md). Číslo rozsahy tyto Unicode kód bodu jsou povolené jako univerzální názvy znaků pro libovolný znak v identifikátoru:  
  
-   00A8, 00AA, 00AD, 00AF, 00B2 00B5, 00B7 00BA, 00BC-00BE 00C 0 AŽ 00 D 6, 8-00F6 00D, 00F8 00FF, 0100-02FF, 0370 167F, 1681 180D, 180F 1DBF, 1E00 1FFF, 200B - 200D, 202A 202E, 203F-2040, 2054 2060-206F, 2070-20CF, 2100-218F, 2460-24FF, 2776-2793 00 2C-2DFF, 2E80 2FFF, 3004 3007, 3021 302F, 3031 303F, 3040-D7FF F900 FD3D, FD40 FDCF, FDF0 FE1F, FE30 FE44, FE47-FFFD 10000 1FFFD, 20000 2FFFD, 30000 3FFFD, 40000 4FFFD, 50000 5FFFD, 60000 6FFFD, 70000 7FFFD, 80000 8FFFD, 90000-9FFFD, A0000-AFFFD, D0000 B0000-BFFFD, C0000-CFFFD-DFFFD, E0000 EFFFD  
  
 Jako libovolný znak v identifikátoru kromě prvního jsou povoleny následující znaky:  
  
```  
0 1 2 3 4 5 6 7 8 9  
```  
  
 Číslo rozsahy tyto Unicode kód bodu jsou povolené také jako univerzální názvy znaků pro libovolný znak v identifikátoru kromě prvního:  
  
-   0300-036F 1DC0 1DFF, 0 20D-20FF, FE20 FE2F  
  
 **Konkrétní Microsoft**  
  
 Pouze první 2 048 znaků identifikátorů Microsoft C++ jsou důležitá. Názvy pro uživatelem definované typy jsou "dekorované" kompilátorem pro zachování informací o typu. Výsledná název, včetně informací o typu, nemůže být delší než 2048 znaků. (Viz [dekorované názvy](../build/reference/decorated-names.md) Další informace.) Faktory ovlivňující délka dekorované identifikátoru jsou:  
  
-   Jestli označuje identifikátor objektu uživatelem definovaný typ nebo typ odvozen od typu definovaný uživatelem.  
  
-   Jestli označuje identifikátor funkci nebo typ odvozený z funkce.  
  
-   Počet argumentů pro funkci.  
  
 Znak dolaru `$` je platný identifikátor znak v jazyce Visual C++. Visual C++ také umožňuje používat skutečnými znaky reprezentována povolených rozsahů univerzální názvy znaků v identifikátory. Pokud chcete používat tyto znaky, musí uložte soubor pomocí kódování znakové stránky, která zahrnuje je souboru.  Tento příklad ukazuje, jak oba rozšířené znaky a univerzální názvy znaků zaměnitelné ve vašem kódu.  
  
```  
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
  
 Rozsah znaků povolených v identifikátoru je méně omezující při kompilování C + +/ CLI kódu. Postupujte podle identifikátory v kódu zkompilovat pomocí/CLR [standardní standardy ECMA-335: společné jazykové infrastruktury (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 **Konkrétní Microsoft END**  
  
 Identifikátor první znak musí být znakem abecedy, velké nebo malé, nebo podtržítkem ( **_** ). Protože jsou identifikátory jazyka C++ velká a malá písmena, `fileName` se liší od `FileName`.  
  
 Identifikátory nesmí být přesně stejnou pravopis a případu jako klíčová slova. Identifikátory, které obsahují klíčová slova jsou právní. Například `Pint` je identifikátor právní, i když obsahuje `int`, což je klíčové slovo.  
  
 Použití dvou po sobě jdoucích podtržítka znaků ( **__** ) na začátku identifikátor nebo jedním úvodní podtržítkem následuje velké písmeno, je vyhrazená pro implementace C++ v všechny obory. Byste neměli používat jeden počáteční podtržítka následuje malé písmeno pro názvech s rozsahem souboru z důvodu možné konflikty s současný nebo budoucí vyhrazené identifikátory.  
  
## <a name="see-also"></a>Viz také  
 [Lexikální konvence](../cpp/lexical-conventions.md)