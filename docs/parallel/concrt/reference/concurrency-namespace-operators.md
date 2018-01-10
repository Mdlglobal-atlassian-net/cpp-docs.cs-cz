---
title: "Concurrency – obor názvů operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs: C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9305f860fb393d2f5d3149300d8df4cfa9f6e5a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-namespace-operators"></a>Concurrency – obor názvů operátory
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operátor&amp;&amp;](#operator_amp_amp)|[operátor&gt;](#operator_gt)|  
|[operátor&gt;=](#operator_gt_eq)|[operátor&lt;](#operator_lt)|[operátor&lt;=](#operator_lt_eq)|  
|[Operator ==](#operator_eq_eq)|[– operátor||](#operator_lor)|  
  
##  <a name="operator_lor"></a>operátor &#124; &#124; Operátor  
 Vytvoří úlohu, která se úspěšně dokončí, když některý z úkolů zadané jako argumenty úspěšně dokončena.  
  
```  
template<typename ReturnType>  
task<ReturnType> operator||(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void> operator||(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>Parametry  
 `ReturnType`  
 Typ vrácený úlohy.  
  
 `lhs`  
 První úlohou se zkombinovat do výsledná úloha.  
  
 `rhs`  
 V druhé úloze se zkombinovat do výsledná úloha.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úloha, která je dokončena úspěšně, pokud některý z vstupní úkolů byla úspěšně dokončena. Pokud vstupní úlohy jsou typu `T`, bude výstup této funkce `task<std::vector<T>`. Pokud vstupní úlohy jsou typu `void` bude také výstup úlohy `task<void>`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud obě akce došlo ke zrušení nebo generování výjimek, vrácený úloha dokončí v zrušené stavu a některé z výjimek, pokud jsou některé došlo, bude vyvolána při volání `get()` nebo `wait()` na úlohu.  
  
##  <a name="operator_amp_amp"></a>operátor&amp; &amp; – operátor  
 Vytvoří úlohu, která se dokončí svou činnost úspěšně, pokud obě úlohy zadané jako argumenty úspěšně dokončit.  
  
```  
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void>  operator&&(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>Parametry  
 `ReturnType`  
 Typ vrácený úlohy.  
  
 `lhs`  
 První úlohou se zkombinovat do výsledná úloha.  
  
 `rhs`  
 V druhé úloze se zkombinovat do výsledná úloha.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úloha, která je dokončena úspěšně, pokud obě vstupu úlohy byly úspěšně dokončeny. Pokud vstupní úlohy jsou typu `T`, bude výstup této funkce `task<std::vector<T>>`. Pokud vstupní úlohy jsou typu `void` bude také výstup úlohy `task<void>`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud některou z úloh je zrušená nebo vyvolá výjimku, vrácený úloha dokončí již v rané fázi, v zrušené stavu, a, pokud je encoutered, dojde k výjimce při volání `get()` nebo `wait()` na úlohu.  
  
##  <a name="operator_eq_eq"></a>Operator == – operátor  
 Pokud testy `concurrent_vector` objekt na levé straně operátoru rovná `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `A1`  
 Typ přidělení první `concurrent_vector` objektu.  
  
 `A2`  
 Typ přidělení druhý `concurrent_vector` objektu.  
  
 `_A`  
 Objekt typu `concurrent_vector`.  
  
 `_B`  
 Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud souběžných vektoru na levé straně operátoru rovná souběžných vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty dvou souběžných vektory jsou si rovny. Jinak nerovné.  
  
 Tato metoda není bezpečná souběžnosti s ohledem na jiné metody, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_neq"></a>Operator! = – operátor  
 Pokud testy `concurrent_vector` objekt na levé straně operátor není rovno `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `A1`  
 Typ přidělení první `concurrent_vector` objektu.  
  
 `A2`  
 Typ přidělení druhý `concurrent_vector` objektu.  
  
 `_A`  
 Objekt typu `concurrent_vector`.  
  
 `_B`  
 Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud není souběžných vektory stejný; `false` Pokud souběžných vektory jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty dvou souběžných vektory jsou si rovny. Jinak nerovné.  
  
 Tato metoda není bezpečná souběžnosti s ohledem na jiné metody, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_lt"></a>operátor&lt; – operátor  
 Testuje, pokud `concurrent_vector` objekt na levé straně operátoru je menší než `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `A1`  
 Typ přidělení první `concurrent_vector` objektu.  
  
 `A2`  
 Typ přidělení druhý `concurrent_vector` objektu.  
  
 `_A`  
 Objekt typu `concurrent_vector`.  
  
 `_B`  
 Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud souběžných vektoru na levé straně operátoru je menší než souběžných vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je stejný jako ekvivalentní operátor pro `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná souběžnosti s ohledem na jiné metody, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_lt_eq"></a>operátor&lt;= – operátor  
 Testuje, pokud `concurrent_vector` objekt na levé straně operátor je menší než nebo rovno `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `A1`  
 Typ přidělení první `concurrent_vector` objektu.  
  
 `A2`  
 Typ přidělení druhý `concurrent_vector` objektu.  
  
 `_A`  
 Objekt typu `concurrent_vector`.  
  
 `_B`  
 Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud souběžných vektoru na levé straně operátoru je menší než nebo rovno souběžných vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je stejný jako ekvivalentní operátor pro `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná souběžnosti s ohledem na jiné metody, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_gt"></a>operátor&gt; – operátor  
 Pokud testy `concurrent_vector` objekt na levé straně operátoru je větší než `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `A1`  
 Typ přidělení první `concurrent_vector` objektu.  
  
 `A2`  
 Typ přidělení druhý `concurrent_vector` objektu.  
  
 `_A`  
 Objekt typu `concurrent_vector`.  
  
 `_B`  
 Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud souběžných vektoru na levé straně operátoru je větší než souběžných vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je stejný jako ekvivalentní operátor pro `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná souběžnosti s ohledem na jiné metody, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_gt_eq"></a>operátor&gt;= – operátor  
 Testuje, pokud `concurrent_vector` objekt na levé straně operátoru je větší než nebo rovno `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `A1`  
 Typ přidělení první `concurrent_vector` objektu.  
  
 `A2`  
 Typ přidělení druhý `concurrent_vector` objektu.  
  
 `_A`  
 Objekt typu `concurrent_vector`.  
  
 `_B`  
 Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud souběžných vektoru na levé straně operátoru je větší než nebo rovno souběžných vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je stejný jako ekvivalentní operátor pro `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná souběžnosti s ohledem na jiné metody, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
