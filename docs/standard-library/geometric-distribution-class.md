---
title: "geometric_distribution – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::geometric_distribution
- random/std::geometric_distribution::reset
- random/std::geometric_distribution::p
- random/std::geometric_distribution::param
- random/std::geometric_distribution::min
- random/std::geometric_distribution::max
- random/std::geometric_distribution::operator()
- random/std::geometric_distribution::param_type
- random/std::geometric_distribution::param_type::p
- random/std::geometric_distribution::param_type::operator==
- random/std::geometric_distribution::param_type::operator!=
dev_langs: C++
helpviewer_keywords:
- std::geometric_distribution [C++]
- std::geometric_distribution [C++], reset
- std::geometric_distribution [C++], p
- std::geometric_distribution [C++], param
- std::geometric_distribution [C++], min
- std::geometric_distribution [C++], max
- std::geometric_distribution [C++], param_type
- std::geometric_distribution [C++], param_type
ms.assetid: 38f933af-3b49-492e-9d26-b6b272a60013
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 796393b3e931cb1afad31809498d329e1a80ad99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="geometricdistribution-class"></a>geometric_distribution – třída
Generuje geometrickou distribuce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class IntType = int>
class geometric_distribution {
public:    
    // types 
    typedef IntType result_type; 
    struct param_type;   
    
    // constructors and reset functions 
    explicit geometric_distribution(double p = 0.5);
    explicit geometric_distribution(const param_type& parm);
    void reset();
    
    // generating functions 
    template <class URNG>  
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);
    
    // property functions 
    double p() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
}; 
```  
#### <a name="parameters"></a>Parametry  
*IntType*  
Výsledný typ celé číslo, výchozí nastavení je `int`. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
*URNG* uniform náhodné číslo generátor modul. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
Šablony třídy popisuje distribuce, která vytváří hodnoty definované uživatelem integrální typu geometrickou rozdělení. Následující tabulka odkazy na články o jednotlivé členy.  
  
||||  
|-|-|-|  
|[geometric_distribution –](#geometric_distribution)|`geometric_distribution::p`|`geometric_distribution::param`|  
|`geometric_distribution::operator()`||[param_type –](#param_type)|  
  
Funkce vlastnost `p()` vrací hodnotu pro parametr uložené distribuční `p`.  
  
Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.  

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.  
  
`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.  
  
`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.
  
Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
Podrobné informace o rozdělení chí-kvadrát, najdete v článku Wolfram MathWorld [geometrickou distribuční](http://go.microsoft.com/fwlink/LinkId=400529).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double p, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::geometric_distribution<> distr(p);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "p() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.p() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double p_dist = 0.5;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'p\' distribution parameter: ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(p_dist, samples);  
}  
```  
  
První test:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'p' distribution parameter: .5
Enter an integer value for the sample count: 100

min() == 0
max() == 2147483647
p() == 0.5000000000
Distribution for 100 samples:
    0 :::::::::::::::::::::::::::::::::::::::::::::::::::::
    1 ::::::::::::::::::::::::::
    2 ::::::::::::
    3 ::::::
    4 ::
    5 :
```  
  
Druhý test:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'p' distribution parameter: .1
Enter an integer value for the sample count: 100

min() == 0
max() == 2147483647
p() == 0.1000000000
Distribution for 100 samples:
    0 :::::::::
    1 :::::::::::
    2 ::::::::::
    3 :::::::
    4 :::::
    5 ::::::::
    6 :::
    7 ::::::
    8 :::::::
    9 :::::
   10 :::
   11 :::
   12 ::
   13 :
   14 :::
   15 ::
   16 :::
   17 :::
   20 :::::
   21 :
   29 :
   32 :
   35 :
```  
  
## <a name="requirements"></a>Požadavky  
**Záhlaví:** \<náhodných >  
  
**Namespace:** – std  
  
##  <a name="geometric_distribution"></a>geometric_distribution::geometric_distribution  
Vytvoří rozdělení.  
  
```  
explicit geometric_distribution(double p = 0.5);
explicit geometric_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*p*  
`p` Distribuční parametr.  
  
*Parametr*  
Struktura parametr použitý k vytvoření distribuce.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou:**`0.0 < p && p < 1.0`  
  
První konstruktoru vytvoří objekt jehož uložené `p` hodnota obsahuje hodnotu *p*.  
  
Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.  
  
##  <a name="param_type"></a>geometric_distribution::param_type  
Ukládá parametry rozdělení.  
  
```  
struct param_type {  
   typedef geometric_distribution<result_type> distribution_type;  
   param_type(double p = 0.5);
   double p() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
  
### <a name="parameters"></a>Parametry  
*p*  
`p` Distribuční parametr.  
  
*vpravo*  
`param_type` Instance k k porovnání.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou:**`0.0 < p && p < 1.0`  
  
Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.  
  
## <a name="see-also"></a>Viz také  
[\<náhodné >](../standard-library/random.md)

