---
title: "Tři tečky a Variadické šablony | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 06b8e0e835cbcb2e2d1b96d5ce861967c7251fca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ellipses-and-variadic-templates"></a>Tři tečky a variadické šablony
Tento článek ukazuje, jak používat se třemi tečkami (`...`) s C++ variadické šablony. Se třemi tečkami zaznamenala mnoho používá jazyka C a C++. Seznamy argumentů proměnných pro funkce patří. `printf()` Funkce z běhové knihovny jazyka C je jedním z dobře známé příklady.  
  
 A *variadické šablony* je šablonu třídy nebo funkce, která podporuje libovolný počet argumentů. Tento mechanismus je obzvláště užitečné pro vývojáře C++ knihovny, protože můžete použít i pro šablony třídy a funkce šablony a tím poskytují širokou škálu bezpečnost typů a nejsou v netriviálních funkcí a větší pružnost.  
  
## <a name="syntax"></a>Syntaxe  
 Tři tečky používá dva způsoby variadické šablony. Nalevo od názvu parametru, označuje *pack parametr*, a vpravo od názvu parametru, rozšíří sady parametrů na názvy.  
  
 Tady je příklad základní *variadické šablony třídy* definice syntaxe:  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 Pro parametr balíčky a rozšíření můžete přidat prázdné kolem se třemi tečkami podle zúčastníte, jak je znázorněno v těchto příkladech:  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 Nebo to:  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 Všimněte si, že tento článek používá konvence, které se zobrazí v prvním příkladu (se třemi tečkami je připojen k `typename`).  
  
 V předchozích ukázkách `Arguments` je sadu parametrů. Třída `classname` může přijmout proměnný počet argumentů, stejně jako tyto příklady:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
  
```  
  
 Pomocí definice třídy variadické šablony můžete také vyžadují minimálně jeden parametr:  
  
```cpp  
template <typename First, typename... Rest> class classname;  
  
```  
  
 Tady je příklad základní *variadické šablony funkce* syntaxe:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 `Arguments` Parametr pack pak rozšířit pro použití, jak je znázorněno v následující části **pochopení variadické šablony**.  
  
 Je možné, jiné formy variadické šablony funkce syntaxe – včetně, mimo jiné tyto příklady:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 Specifikátory jako `const` jsou povoleny také:  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
  
```  
  
 Jako s definice tříd variadické šablony, můžete provést funkcí, které vyžadují minimálně jeden parametr:  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
  
```  
  
 Použít Variadické šablony `sizeof...()` – operátor (který nesouvisí se starší `sizeof()` operátor):  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    constexpr auto numargs{ sizeof...(Arguments) };  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
  
```  
  
## <a name="more-about-ellipsis-placement"></a>Další informace o umístění třemi tečkami  
 Dříve, tento článek popisuje třemi tečkami umístění definující parametr balíčky a rozšiřuje jako "nalevo od názvu parametru, se označuje sadu parametrů a vpravo od názvu parametru, rozšíří sady parametrů na názvy". To je technicky hodnota true, ale může být matoucí v překlad kódu. Vezměte v úvahu:  
  
-   V šabloně parametr seznamu (`template <parameter-list>`), `typename...` představuje sadu parametrů šablony.  
  
-   Parametr deklarace – klauzule (`func(parameter-list)`), "nejvyšší úrovně" třemi tečkami představuje sadu parametrů funkce a třemi tečkami umístění je důležité:  
  
    ```cpp  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   Kde se třemi tečkami se zobrazí okamžitě po název parametru, máte rozšíření pack parametr.  
  
## <a name="example"></a>Příklad  
 Dobrým způsobem, jak znázorňují mechanismus variadické šablony funkce je pro použití v znovu zápis některých funkcí `printf`:  
  
```cpp  
#include <iostream>  
  
using namespace std;  
  
void print() {  
    cout << endl;  
}  
  
template <typename T> void print(const T& t) {  
    cout << t << endl;  
}  
  
template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {  
    cout << first << ", ";  
    print(rest...); // recursive call using pack expansion syntax  
}  
  
int main()  
{  
    print(); // calls first overload, outputting only a newline  
    print(1); // calls second overload  
  
    // these call the third overload, the variadic template,   
    // which uses recursion as needed.  
    print(10, 20);  
    print(100, 200, 300);  
    print("first", 2, "third", 3.14159);  
}  
  
```  
  
## <a name="output"></a>Výstup  
  
```  
  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  Většinu implementací, které zahrnout variadické šablony funkce používat rekurze některé formuláře, ale se mírně liší od tradiční rekurze.  Tradiční rekurze zahrnuje funkce volání samotné pomocí stejným podpisem. (To může být přetížené nebo podle šablony, ale stejným podpisem je zvolen pokaždé, když.) Variadická rekurze zahrnuje volání šablony funkce variadická pomocí (téměř vždy klesá) různý počet argumentů, a tím časového razítka na jiný podpis pokaždé, když. "Základní případ" není stále požadována, ale povaha rekurze se liší.  
  
