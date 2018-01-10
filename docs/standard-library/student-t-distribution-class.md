---
title: "student_t_distribution – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::student_t_distribution
- random/std::student_t_distribution::result_type
- random/std::student_t_distribution::reset
- random/std::student_t_distribution::operator()
- random/std::student_t_distribution::n
- random/std::student_t_distribution::param
- random/std::student_t_distribution::min
- random/std::student_t_distribution::max
- random/std::student_t_distribution::param_type
dev_langs: C++
helpviewer_keywords:
- std::student_t_distribution [C++]
- std::student_t_distribution [C++], result_type
- std::student_t_distribution [C++], reset
- std::student_t_distribution [C++], n
- std::student_t_distribution [C++], param
- std::student_t_distribution [C++], min
- std::student_t_distribution [C++], max
- std::student_t_distribution [C++], param_type
ms.assetid: 87b48127-9311-4d07-95df-833ed46bf0b1
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f611d9c7093006a5212c68096aecd4b723086e4c
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="studenttdistribution-class"></a>student_t_distribution – třída
Generuje Studentova *t*-distribuce.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class RealType = double>
class student_t_distribution {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   explicit student_t_distribution(result_type n = 1.0);
   explicit student_t_distribution(const param_type& parm);
   void reset();
   
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   
   // property functions  
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
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje distribuce, která vytváří hodnoty integrální se zadán uživatel nebo typu `double` Pokud žádný je k dispozici, distribuovat podle Studentova *t*-distribuční. Následující tabulka odkazy na články o jednotlivé členy.  
  
||||  
|-|-|-|  
|[student_t_distribution](#student_t_distribution)|`student_t_distribution::n`|`student_t_distribution::param`|  
|`student_t_distribution::operator()`||[param_type –](#param_type)|  
  
 Funkce vlastnost `n()` vrací hodnotu pro parametr uložené distribuční `n`.  
  
 Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
 Podrobné informace o Studentova *t*-distribuci, najdete v článku Wolfram MathWorld [studenty t rozdělení](http://go.microsoft.com/fwlink/p/?linkid=401094).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double n, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::student_t_distribution<> distr(n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
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
    double n_dist = 0.5;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'n' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(n_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: -1.3084956212  
    2: -1.0899518684  
    3: -0.9568771388  
    4: -0.9372088821  
    5: -0.7381334669  
    6: -0.2488074854  
    7: -0.2028714601  
    8: 1.4013074495  
    9: 5.3244792236  
    10: 92.7084335614  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<náhodných >  
  
 **Namespace:** – std  
  
##  <a name="student_t_distribution"></a>student_t_distribution::student_t_distribution  
 Vytvoří rozdělení.  
  
```  
explicit student_t_distribution(RealType n = 1.0);
explicit student_t_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*n*  
 `n` Distribuční parametr.  
  
*Parametr*  
 Balíček parametr použitý k vytvoření distribuce.  
  
### <a name="remarks"></a>Poznámky  
 **Předběžnou:**`0.0 < n`  
  
 První konstruktoru vytvoří objekt jehož uložené `n` hodnota obsahuje hodnotu  *n* .  
  
 Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.  
  
##  <a name="param_type"></a>student_t_distribution::param_type  
 Uloží všechny parametry rozdělení.  
```cpp    
struct param_type {  
   typedef student_t_distribution<result_type> distribution_type;  
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
  
### <a name="parameters"></a>Parametry  
*n*  
`n` Distribuční parametr.  
  
*vpravo*  
`param_type` Objekt k porovnání s to.  
  
### <a name="remarks"></a>Poznámky  
 **Předběžnou:**`0.0 < n`  
  
 Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.  
  
## <a name="see-also"></a>Viz také  
 [\<náhodné >](../standard-library/random.md)



