---
title: "bernoulli_distribution – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
dev_langs: C++
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd4d0e5e5fb88eae5ca0247f1672e816dc35c601
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bernoullidistribution-class"></a>bernoulli_distribution – třída
Generuje Bernoulliho distribuce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class bernoulli_distribution  
   {  
public:  
   // types  
   typedef bool result_type;  
   struct param_type;  

   // constructors and reset functions  
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
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
  
### <a name="parameters"></a>Parametry  
  
*URNG* uniform náhodné číslo generátor modul. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
Třída popisuje distribuce, která vytváří hodnoty typu `bool`distribuovaná podle Bernoulliho distribuční diskrétní pravděpodobnosti funkci. Následující tabulka odkazy na články o jednotlivé členy.  
  
||||  
|-|-|-|  
|[bernoulli_distribution –](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|  
|`bernoulli_distribution::operator()`||[param_type –](#param_type)|  
  
Vlastnost člena `p()` vrátí hodnotu parametru aktuálně uložené distribuční `p`.  
  
Vlastnost člena `param()` Nastaví nebo vrátí `param_type` balíček parametr uložené distribuce.  

`min()` a `max()` členské funkce vrátí nejmenší možný výsledek a největší možné výsledek, v uvedeném pořadí.  
  
`reset()` – Členská funkce zahodí všechny hodnoty v mezipaměti, aby výsledkem další volání `operator()` nezávisí na žádné hodnoty získané z modulu před voláním.  
  
`operator()` Členské funkce vrátí další generované hodnoty, které jsou založené na modulu URNG buď z aktuální parametr balíček nebo balíček zadaný parametr.
  
Další informace o distribučních třídy a jejich členové najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
Podrobné informace o funkci diskrétní pravděpodobnosti Bernoulliho distribuce, najdete v článku Wolfram MathWorld [Bernoulliho distribuční](http://go.microsoft.com/fwlink/LinkId=398467).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double p, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::bernoulli_distribution distr(p);  
  
    std::cout << "p == " << distr.p() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<bool, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Histogram for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double p_dist = 0.5;  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for a sample count: ";  
    std::cin >> samples;  
  
    test(p_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45  
Enter an integer value for a sample count: 100  
p == 0.45  
Histogram for 100 samples:  
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
 true :::::::::::::::::::::::::::::::::::::::::
```  
  
## <a name="requirements"></a>Požadavky  
**Záhlaví:** \<náhodných >  
  
**Namespace:** – std  
  
##  <a name="bernoulli_distribution"></a>bernoulli_distribution::bernoulli_distribution  
Vytvoří rozdělení.  
  
```  
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*p*  
 Uložených `p` distribuční parametr.  
  
*Parametr*  
 `param_type` Struktura použitý k vytvoření distribuce.  
  
### <a name="remarks"></a>Poznámky  
 **Předběžnou:**`0.0 ≤ p ≤ 1.0`  
  
První konstruktoru vytvoří objekt jehož uložené `p` hodnota obsahuje hodnotu *p*.  
  
Druhý konstruktor vytvoří objekt, jehož uložené parametry jsou inicializovány z *parametr*. Můžete získat a nastavit aktuální parametry existující distribuční voláním `param()` – členská funkce.  
  
##  <a name="param_type"></a>bernoulli_distribution::param_type  
Obsahuje parametry rozdělení.  
  
{param_type – struktura  
   distribution_type – TypeDef bernoulli_distribution –;  
   param_type – (dvakrát p = 0,5); dvojité p() const;

   BOOL – operátor == (const param_type – & doprava) const; BOOL – operátor! = (const param_type – & doprava) const; };  
  
### <a name="parameters"></a>Parametry  
*p*  
Uložených `p` distribuční parametr.  
  
### <a name="remarks"></a>Poznámky  
**Předběžnou:**`0.0 ≤ p ≤ 1.0`  
  
Tato struktura mohou být předána do konstruktoru třídy distribuční při vytváření instancí, položky `param()` – členská funkce nastavit uložené parametrů z existující distribuční a to `operator()` má být použit místo uložené parametry.  
  
## <a name="see-also"></a>Viz také  
 [\<náhodné >](../standard-library/random.md)


