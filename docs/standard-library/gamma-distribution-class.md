---
title: "gamma_distribution – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::gamma_distribution
- random/std::gamma_distribution::reset
- random/std::gamma_distribution::alpha
- random/std::gamma_distribution::beta
- random/std::gamma_distribution::param
- random/std::gamma_distribution::min
- random/std::gamma_distribution::max
- random/std::gamma_distribution::operator()
- random/std::gamma_distribution::param_type
- random/std::gamma_distribution::param_type::alpha
- random/std::gamma_distribution::param_type::beta
- random/std::gamma_distribution::param_type::operator==
- random/std::gamma_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::gamma_distribution [C++]
- std::gamma_distribution [C++], reset
- std::gamma_distribution [C++], alpha
- std::gamma_distribution [C++], beta
- std::gamma_distribution [C++], param
- std::gamma_distribution [C++], min
- std::gamma_distribution [C++], max
- std::gamma_distribution [C++], param_type
- std::gamma_distribution [C++], param_type
ms.assetid: 2a6798ac-6152-41d7-8ef6-d684d92f1572
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3cb7f844a579dced503186f8d786aef0fb6cd2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="gammadistribution-class"></a>gamma_distribution – třída
Generuje gama rozdělení.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class RealType = double>
class gamma_distribution {
public:    
    // types 
    typedef RealType result_type;    
    struct param_type;  

    // constructors and reset functions 
    explicit gamma_distribution(result_type alpha = 1.0, result_type beta = 1.0);
    explicit gamma_distribution(const param_type& parm);
    void reset();
    
    // generating functions
    template <class URNG>  
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);
    
    // property functions
    result_type alpha() const;
    result_type beta() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```    
#### <a name="parameters"></a>Parametry  
*RealType*  
Použije se výchozí hodnota s plovoucí desetinnou čárkou výsledný typ, `double`. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
*URNG* uniform náhodné číslo generátor modul. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
Šablony třídy popisuje distribuce, která vytváří hodnoty definované uživatelem s plovoucí desetinnou čárkou nebo typu `double` Pokud žádný je k dispozici, distribuovat podle gama rozdělení. Následující tabulka odkazy na články o jednotlivé členy.  
  
||||  
|-|-|-|  
|[gamma_distribution](#gamma_distribution)|`gamma_distribution::alpha`|`gamma_distribution::param`|  
|`gamma_distribution::operator()`|`gamma_distribution::beta`|[param_type](#param_type)|  
  
Funkce vlastností `alpha()` a `beta()` vrátit jejich příslušné hodnoty pro parametry uložené distribuční *alpha* a *beta*.  
  
Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.  

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.  
  
`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.  
  
`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.
  
Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
Podrobné informace o rozdělení gama, najdete v článku Wolfram MathWorld [gama rozdělení](http://go.microsoft.com/fwlink/p/?linkid=401111).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double a, const double b, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
  
    std::mt19937 gen(1701);  
  
    std::gamma_distribution<> distr(a, b);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "alpha() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.alpha() << std::endl;  
    std::cout << "beta() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.beta() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<double, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        std::cout << std::fixed << std::setw(11) << ++counter << ": "  
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double a_dist = 0.0;  
    double b_dist = 1;  
  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
alpha() == 1.0000000000  
beta() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0936880533  
    2: 0.1225944894  
    3: 0.6443593183  
    4: 0.6551171649  
    5: 0.7313457551  
    6: 0.7313557977  
    7: 0.7590097389  
    8: 1.4466885214  
    9: 1.6434088411  
    10: 2.1201210996  
```  
  
## <a name="requirements"></a>Požadavky  
**Záhlaví:** \<náhodných >  
  
**Namespace:** – std  
  
##  <a name="gamma_distribution"></a>  gamma_distribution::gamma_distribution  
Vytvoří rozdělení.  
  
```  
explicit gamma_distribution(result_type alpha = 1.0, result_type beta = 1.0);
explicit gamma_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*alpha*  
`alpha` Distribuční parametr.  
  
*beta*  
`beta` Distribuční parametr.  
  
*parm*  
Struktura parametr použitý k vytvoření distribuce.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou:** `0.0 < alpha` a `0.0 < beta`  
  
První konstruktoru vytvoří objekt jehož uložené `alpha` hodnota obsahuje hodnotu *alpha* a jehož uložené `beta` hodnota obsahuje hodnotu *beta*.  
  
Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.  
  
##  <a name="param_type"></a>  gamma_distribution::param_type  
Ukládá parametry rozdělení.  
  
```cpp   
struct param_type {  
   typedef gamma_distribution<result_type> distribution_type;  
   param_type(result_type alpha = 1.0, result_type beta 1.0);
   result_type alpha() const;
   result_type beta() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>Parametry  
*alpha*  
`alpha` Distribuční parametr.  
  
*beta*  
`beta` Distribuční parametr.  
  
Vpravo  
`param_type` Instance k k porovnání.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou:** `0.0 < alpha` a `0.0 < beta`  
  
Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.  
  
## <a name="see-also"></a>Viz také  
[\<random>](../standard-library/random.md)



