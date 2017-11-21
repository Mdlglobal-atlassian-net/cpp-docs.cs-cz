---
title: "Operátory obor názvů souběžnosti (AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cc8e24c8fd1524ebaaf6c2a8edaec05ab865733
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-namespace-operators-amp"></a>Operátory obor názvů souběžnosti (AMP)
||||  
|-|-|-|  
|[Operator! =](#operator_neq)|[% – operátor](#operator_mod)|[operátor *](#operator_star)|  
|[operátor +](#operator_add)|[Operator –](#operator-)|[operátor nebo](#operator_div)|  
|[Operator ==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>Operator ==   
 Určuje, zda jsou zadané argumenty jsou stejné.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Jeden z řazené kolekce členů k porovnání.  
  
 `_Rhs`  
 Jeden z řazené kolekce členů k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud jsou řazené kolekce členů stejné; v opačném `false`.  
  
##  <a name="operator_neq"></a>Operator! =   
 Určuje, zda jsou zadané argumenty nejsou stejné.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Jeden z řazené kolekce členů k porovnání.  
  
 `_Rhs`  
 Jeden z řazené kolekce členů k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud řazené kolekce členů nejsou stejné; v opačném `false`.  
  
##  <a name="operator_add"></a>operátor +   

 Vypočítá component-wise součet jsou zadané argumenty.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Jeden z argumentů pro přidání.  
  
 `_Rhs`  
 Jeden z argumentů pro přidání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Component-wise součet jsou zadané argumenty.  
  
##  <a name="operator-"></a>Operator –   

 Vypočítá component-wise rozdíl mezi zadanými argumenty.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Argument bude odečítat od.  
  
 `_Rhs`  
 Argument má odečíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Component-wise rozdíl mezi zadanými argumenty.  
  
##  <a name="operator_star"></a>operátor *   

 Vypočítá component-wise produkt jsou zadané argumenty.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Jeden z mají vynásobit řazené kolekce členů.  
  
 `_Rhs`  
 Jeden z mají vynásobit řazené kolekce členů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Component-wise produktu jsou zadané argumenty.  
  

##  <a name="operator_div"></a>operátor nebo   
 Vypočítá component-wise podíl jsou zadané argumenty.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Rozdělit řazené kolekce členů.  
  
 `_Rhs`  
 Pokus dělit řazené kolekce členů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Component-wise podíl jsou zadané argumenty.  
  
##  <a name="operator_mod"></a>% – operátor   

 Vypočítá zbytek z první argument zadaný ve druhém zadaného argumentu.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Pořadí argumentů řazené kolekce členů.  
  
 `_Lhs`  
 Řazené kolekce členů ze kterého modulo se počítá.  
  
 `_Rhs`  
 N-tice k modulo podle.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek první numerického zbytku zadaného argumentu druhý zadaného argumentu.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace-cpp-amp.md)
