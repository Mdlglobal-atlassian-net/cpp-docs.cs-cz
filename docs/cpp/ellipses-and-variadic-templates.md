---
title: Tři tečky a Variadické šablony | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45dc0dfe85e7693cdea9c6e469ff347d75c13d57
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402943"
---
# <a name="ellipses-and-variadic-templates"></a>Tři tečky a variadické šablony
Tento článek ukazuje, jak použít tři tečky (`...`) s šablonami variadic jazyka C++. Tři tečky měly celou řadu uplatnění v jazyce C a C++. Patří sem variabilní seznamy proměnných pro funkce. `printf()` Funkce běhové knihovny jazyka C je jedním z nejlépe známých příkladů.  
  
 A *variadické šablony* je šablona třídy nebo funkce, která podporuje libovolný počet argumentů. Tento mechanismus je užitečné zejména pro vývojáře knihovny C++, protože platí pro šablony třídy i šablon funkcí a tím poskytnout širokou škálu zajišťující bezpečnost typů a nejsou v netriviálních funkcí a flexibility.  
  
## <a name="syntax"></a>Syntaxe  
 Variadické šablony používá dvě možnosti, jak tři tečky. Nalevo od názvu parametru, označuje *balíček parametrů*, a napravo od názvu parametru rozšiřuje sady parametrů na oddělené názvy.  
  
 Tady je příklad základní *variadické šablony třídy* syntaxe definice:  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 Sadami parametrů a rozšíření můžete přidat mezery kolem se třemi tečkami, podle dáváte přednost, jak je znázorněno v těchto příkladech:  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 Nebo to:  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 Všimněte si, že tento článek používá konvenci, která se zobrazí v prvním příkladu (tři tečky je připojen k `typename`).  
  
 V předchozích ukázkách *argumenty* je balíčkem parametrů. Třída `classname` může přijímat proměnný počet argumentů, jako v těchto příkladech:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
```  
  
 Pomocí definice tříd variadických šablon můžete také vyžadovat nejméně jeden parametr:  
  
```cpp  
template <typename First, typename... Rest> class classname;  
```  
  
 Tady je příklad základní *variadické šablony funkce* syntaxi:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 *Argumenty* balíček parametrů je pak rozšířen pro potřeby použití, jak je znázorněno v následující části **Princip variadických šablon**.  
  
 Jiné formy syntaxe variadických funkcí šablon jsou možné – včetně, ale nikoli výhradně, tyto příklady:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 Specifikátory jako **const** jsou také povoleny:  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
```  
  
 Jako s definicí tříd variadických šablon, můžete vytvořit funkce, které vyžadují nejméně jeden parametr:  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
```  
  
 Variadické šablony používají `sizeof...()` – operátor (nesouvisející se starším `sizeof()` operátor):  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    constexpr auto numargs{ sizeof...(Arguments) };  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
```  
  
## <a name="more-about-ellipsis-placement"></a>Další informace o umístění tlačítko se třemi tečkami  
 Dříve, tento článek popisuje tři tečky umístění, která definuje sadami parametrů a rozšíření jako "nalevo od názvu parametru, označuje sadu parametrů a napravo od názvu parametru rozšiřuje sady parametrů na oddělené názvy". To je technicky hodnotu true, ale může být matoucí, v překladu do kódu. Vezměte v úvahu:  
  
-   V šabloně parameter-list (`template <parameter-list>`), `typename...` zavádí balíček parametrů šablony.  
  
-   V parametru deklarace – klauzule (`func(parameter-list)`), balíček parametrů funkce zavádí "nejvyšší úrovně" tři tečky a tlačítko se třemi tečkami umístění je důležité:  
  
    ```cpp  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   Pokud na symbol tří teček se zobrazí okamžitě po názvu parametru, je nutné rozšíření balíčku parametrů.  
  
## <a name="example"></a>Příklad  
 Dobrým způsobem ke znázornění mechanismu funkce variadické šablony je jeho použití v přepsání některých funkcí `printf`:  
  
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
  
```Output  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  Většina implementací, které funkce variadické šablony pomocí rekurze některé formuláře, ale se mírně liší od tradičních rekurze.  Tradiční rekurze zahrnuje funkci volající sama sebe pomocí stejného podpisu. (To může být přetížené nebo bez vizuálního vzhledu, ale je vybrána stejná signatura pokaždé, když.) Variadická rekurze zahrnuje volání šablony variadické funkce pomocí odlišných (téměř vždy snížení) počtu argumentů a tím orazítkování jiného podpisu při každém. "Základní případ" je nutné použít, ale povaha rekurze se liší.  