---
title: "normal_distribution – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::normal_distribution
- random/std::normal_distribution::reset
- random/std::normal_distribution::mean
- random/std::normal_distribution::stddev
- random/std::normal_distribution::param
- random/std::normal_distribution::min
- random/std::normal_distribution::max
- random/std::normal_distribution::operator()
- random/std::normal_distribution::param_type
- random/std::normal_distribution::param_type::mean
- random/std::normal_distribution::param_type::stddev
- random/std::normal_distribution::param_type::operator==
- random/std::normal_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::normal_distribution [C++]
- std::normal_distribution [C++], reset
- std::normal_distribution [C++], mean
- std::normal_distribution [C++], stddev
- std::normal_distribution [C++], param
- std::normal_distribution [C++], min
- std::normal_distribution [C++], max
- std::normal_distribution [C++], param_type
- std::normal_distribution [C++], param_type
ms.assetid: bf92cdbd-bc72-4d4a-b588-173d748f0d7d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a3d4de1e2316c2a406d6e2a3278c60c214201aa
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="normaldistribution-class"></a>normal_distribution – třída
Generuje normálního rozdělení.  
  
## <a name="syntax"></a>Syntaxe  
```  
template<class RealType = double>
class normal_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  

   // constructors and reset functions  
   explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
   explicit normal_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   result_type mean() const;
   result_type stddev() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
  
### <a name="parameters"></a>Parametry  
*RealType*  
Použije se výchozí hodnota s plovoucí desetinnou čárkou výsledný typ, `double`. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
Šablony třídy popisuje distribuce, která vytváří hodnoty integrální se zadán uživatel nebo typu `double` Pokud žádný je k dispozici, distribuovat podle normálního rozdělení. Následující tabulka odkazy na články o jednotlivé členy.  
  
||||  
|-|-|-|  
|[normal_distribution](#normal_distribution)|`normal_distribution::mean`|`normal_distribution::param`|  
|`normal_distribution::operator()`|`normal_distribution::stddev`|[param_type](#param_type)|  
  
Funkce vlastností `mean()` a `stddev()` návratové hodnoty pro parametry uložené distribuční `mean` a `stddev` v uvedeném pořadí.  
  
Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.  

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.  
  
`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.  
  
`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.
  
Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
Podrobné informace o normálního rozdělení, najdete v článku Wolfram MathWorld [normálního rozdělení](http://go.microsoft.com/fwlink/p/?linkid=400924).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const double m, const double s, const int samples) {  
  
    // uncomment to use a non-deterministic seed  
    //    random_device gen;  
    //    mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    normal_distribution<> distr(m, s);  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.mean() << endl;  
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.stddev() << endl;  
  
    // generate the distribution as a histogram  
    map<double, int> histogram;  
    for (int i = 0; i < samples; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << samples << " samples:" << endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        cout << fixed << setw(11) << ++counter << ": "  
            << setw(14) << setprecision(10) << elem.first << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    double m_dist = 1;  
    double s_dist = 1;  
    int samples = 10;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter a floating point value for the 'mean' distribution parameter: ";  
    cin >> m_dist;  
    cout << "Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): ";  
    cin >> s_dist;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(m_dist, s_dist, samples);  
}  
  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'mean' distribution parameter: 0  
Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
m() == 0.0000000000  
s() == 1.0000000000  
Distribution for 10 samples:  
    1: -0.8845823965  
    2: -0.1995761116  
    3: -0.1162665130  
    4: -0.0685154932  
    5: 0.0403741461  
    6: 0.1591327792  
    7: 1.0414389924  
    8: 1.5876269426  
    9: 1.6362637713  
    10: 2.7821317338  
```  
  
## <a name="requirements"></a>Požadavky  
**Záhlaví:** \<náhodných >  
  
**Namespace:** – std  
  
##  <a name="normal_distribution"></a>  normal_distribution::normal_distribution  
Vytvoří rozdělení.  
  
```  
explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
explicit normal_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*střední*  
`mean` Distribuční parametr.  
  
*stddev*  
`stddev` Distribuční parametr.  
  
*parm*  
Struktura parametr použitý k vytvoření distribuce.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou podmínku:** `0.0 ≤ stddev`  
  
První konstruktoru vytvoří objekt jehož uložené `mean` hodnota obsahuje hodnotu *znamenat* a jehož uložené `stddev` hodnota obsahuje hodnotu *stddev*.  
  
Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.  
  
##  <a name="param_type"></a>  normal_distribution::param_type  
Ukládá parametry rozdělení.  
  
```cpp  
struct param_type {  
   typedef normal_distribution<result_type> distribution_type;  
   param_type(result_type mean = 0.0, result_type stddev = 1.0);
   result_type mean() const;
   result_type stddev() const;
  
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>Parametry  
*střední*  
`mean` Distribuční parametr.  
  
*stddev*  
`stddev` Distribuční parametr.  
  
Vpravo  
`param_type` Struktura použit k porovnání.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou podmínku:** `0.0 ≤ stddev`  
  
Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.  
  
## <a name="see-also"></a>Viz také  
 [\<random>](../standard-library/random.md)



