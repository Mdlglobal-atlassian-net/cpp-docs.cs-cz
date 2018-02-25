---
title: "fisher_f_distribution – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::fisher_f_distribution
- random/std::fisher_f_distribution::reset
- random/std::fisher_f_distribution::m
- random/std::fisher_f_distribution::n
- random/std::fisher_f_distribution::param
- random/std::fisher_f_distribution::min
- random/std::fisher_f_distribution::max
- random/std::fisher_f_distribution::operator()
- random/std::fisher_f_distribution::param_type
- random/std::fisher_f_distribution::param_type::m
- random/std::fisher_f_distribution::param_type::n
- random/std::fisher_f_distribution::param_type::operator==
- random/std::fisher_f_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::fisher_f_distribution [C++]
- std::fisher_f_distribution [C++], reset
- std::fisher_f_distribution [C++], m
- std::fisher_f_distribution [C++], n
- std::fisher_f_distribution [C++], param
- std::fisher_f_distribution [C++], min
- std::fisher_f_distribution [C++], max
- std::fisher_f_distribution [C++], param_type
- std::fisher_f_distribution [C++], param_type
ms.assetid: 9513b6ce-3309-4be1-829b-f504bca35bbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 232edd9e13d0a58f42a11d1450383adb0f7e8fb2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="fisherfdistribution-class"></a>fisher_f_distribution – třída
Generuje Fisherovy F distribuce.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class RealType = double>
class fisher_f_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  // constructor and reset functions  
   explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
   explicit fisher_f_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   result_type m() const;
   result_type n() const;
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
 Šablony třídy popisuje distribuce, která vytváří hodnoty definované uživatelem s plovoucí desetinnou čárkou nebo typu `double` Pokud žádný je k dispozici, distribuovat podle Fisherovy F-rozdělení. Následující tabulka odkazy na články o jednotlivé členy.  
  
||||  
|-|-|-|  
|[fisher_f_distribution](#fisher_f_distribution)|`fisher_f_distribution::m`|`fisher_f_distribution::param`|  
|`fisher_f_distribution::operator()`|`fisher_f_distribution::n`|[param_type](#param_type)|  
  
 Funkce vlastností `m()` a `n()` návratové hodnoty pro parametry uložené distribuční `m` a `n` v uvedeném pořadí.  
  
Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.  

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.  
  
`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.  
  
`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.
  
 Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
 Podrobné informace o rozdělení F, najdete v článku Wolfram MathWorld [F-rozdělení](http://go.microsoft.com/fwlink/p/?linkid=400899).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double m, const double n, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1701);  
  
    std::fisher_f_distribution<> distr(m, n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "m() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.m() << std::endl;  
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;  
  
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
    double m_dist = 1;  
    double n_dist = 1;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'m\' distribution parameter (must be greater than zero): ";  
    std::cin >> m_dist;  
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(m_dist, n_dist, samples);  
}  
  
```  
  
## <a name="output"></a>Výstup  
 Nejprve spusťte:  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0204569549  
    2: 0.0221376644  
    3: 0.0297234962  
    4: 0.1600937252  
    5: 0.2775342196  
    6: 0.3950701700  
    7: 0.8363200295  
    8: 0.9512500702  
    9: 2.7844815974  
    10: 3.4320929653  
```  
  
 Druhý spusťte:  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 0.1000000000  
Distribution for 10 samples:  
    1: 0.0977725649  
    2: 0.5304122767  
    3: 4.9468518084  
    4: 25.1012074939  
    5: 48.8082121613  
    6: 401.8075539377  
    7: 8199.5947873699  
    8: 226492.6855335717  
    9: 2782062.6639740225  
    10: 20829747131.7185860000  
```  
  
 Třetí spusťte:  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): .1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 0.1000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0000000000  
    2: 0.0000000000  
    3: 0.0000000000  
    4: 0.0000000000  
    5: 0.0000000033  
    6: 0.0000073975  
    7: 0.0000703800  
    8: 0.0280427735  
    9: 0.2660239949  
    10: 3.4363333954  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<náhodných >  
  
 **Namespace:** – std  
  
##  <a name="fisher_f_distribution"></a>  fisher_f_distribution::fisher_f_distribution  
 Vytvoří rozdělení.  
  
```  
explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
explicit fisher_f_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*m*  
 `m` Distribuční parametr.  
  
*n*  
 `n` Distribuční parametr.  
  
*parm*  
 `param_type` Struktura použitý k vytvoření distribuce.  
  
### <a name="remarks"></a>Poznámky  
 **Předběžnou:** `0.0 < m` a `0.0 < n`  
  
 První konstruktoru vytvoří objekt jehož uložené `m` hodnota obsahuje hodnotu *m* a jehož uložené `n` hodnota obsahuje hodnotu  *n* .  
  
 Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.  
  
##  <a name="param_type"></a>  fisher_f_distribution::param_type  
 Ukládá parametry rozdělení.  
  
```cpp  
struct param_type {  
   typedef fisher_f_distribution<result_type> distribution_type;  
   param_type(result_type m = 1.0, result_type n = 1.0);
   result_type m() const;
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>Parametry  
*m*  
 `m` Distribuční parametr.  
  
*n*  
 `n` Distribuční parametr.  
  
Vpravo  
`param_type` Objekt k porovnání s to.  
  
### <a name="remarks"></a>Poznámky  
 **Předběžnou:** `0.0 < m` a `0.0 < n`  
  
 Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.  
  
## <a name="see-also"></a>Viz také  
 [\<random>](../standard-library/random.md)



