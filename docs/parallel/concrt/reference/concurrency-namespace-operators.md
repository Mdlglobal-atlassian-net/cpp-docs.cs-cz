---
title: Concurrency – operátory oboru názvů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13b9288e39e372ecb23299d355abc921353444b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059869"
---
# <a name="concurrency-namespace-operators"></a>Concurrency – operátory oboru názvů
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[– Operátor&amp;&amp;](#operator_amp_amp)|[– Operátor&gt;](#operator_gt)|  
|[– Operátor&gt;=](#operator_gt_eq)|[– Operátor&lt;](#operator_lt)|[– Operátor&lt;=](#operator_lt_eq)|  
|[operator==](#operator_eq_eq)|[– operátor||](#operator_lor)|  
  
##  <a name="operator_lor"></a>  operátor&#124; &#124; – operátor  
 Vytvoří úlohu, která bude dokončena úspěšně, pokud jeden z úkolů zadané jako argumenty úspěšně dokončena.  
  
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
*Vlastnost ReturnType*<br/>
Typ vrácené úlohy.  
  
*lhs*<br/>
První úkol ke sloučení do výsledného úkolu.  
  
*Zarovnání indirekce RHS*<br/>
Druhý úkol ke sloučení do výsledného úkolu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úloha, která se úspěšně dokončí, když některý vstupní úlohy byla úspěšně dokončena. Pokud jsou vstupní úlohy typu `T`, bude výstup této funkce `task<std::vector<T>`. Pokud jsou vstupní úlohy typu `void` výstupní úloha bude také `task<void>`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud obě úlohy zrušení nebo vyvolat výjimku, vrácené úlohy budou dokončeny ve zrušeném stavu a jednu z výjimek, pokud nedojde k žádné jsou, bude vyvolána výjimka při volání `get()` nebo `wait()` pro tento úkol.  
  
##  <a name="operator_amp_amp"></a>  operátor&amp; &amp; – operátor  
 Vytvoří úlohu, která bude dokončena úspěšně, pokud obě úlohy uvedené jako argumenty úspěšně dokončena.  
  
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
*Vlastnost ReturnType*<br/>
Typ vrácené úlohy.  
  
*lhs*<br/>
První úkol ke sloučení do výsledného úkolu.  
  
*Zarovnání indirekce RHS*<br/>
Druhý úkol ke sloučení do výsledného úkolu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úloha, která se úspěšně dokončí, když oba vstupní úkoly byly úspěšně dokončeny. Pokud jsou vstupní úlohy typu `T`, bude výstup této funkce `task<std::vector<T>>`. Pokud jsou vstupní úlohy typu `void` výstupní úloha bude také `task<void>`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jeden z úkolů zrušen nebo vyvolá výjimku, vrácené úlohy budou dokončeny včas ve zrušeném stavu a, pokud je encoutered, bude vyvolána výjimka při volání `get()` nebo `wait()` pro tento úkol.  
  
##  <a name="operator_eq_eq"></a>  Operator == – operátor  
 Testuje, zda `concurrent_vector` objekt na levé straně operátoru rovná `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků uložených v souběžné vektorů.  
  
*A1*<br/>
Typ alokátoru prvního `concurrent_vector` objektu.  
  
*A2*<br/>
Typ alokátoru druhého `concurrent_vector` objektu.  
  
*_A*<br/>
Objekt typu `concurrent_vector`.  
  
*_B*<br/>
Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je souběžného vektoru na levé straně operátoru roven souběžného vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Dva vektory souběžných jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.  
  
 Tato metoda není bezpečná pro souběžnost s ohledem na dalších metodách, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_neq"></a>  Operator! = – operátor  
 Testuje, zda `concurrent_vector` objekt na levé straně operátoru není roven `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků uložených v souběžné vektorů.  
  
*A1*<br/>
Typ alokátoru prvního `concurrent_vector` objektu.  
  
*A2*<br/>
Typ alokátoru druhého `concurrent_vector` objektu.  
  
*_A*<br/>
Objekt typu `concurrent_vector`.  
  
*_B*<br/>
Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud souběžných vektory nejsou stejné; `false` Pokud jsou souběžný vektory stejné.  
  
### <a name="remarks"></a>Poznámky  
 Dva vektory souběžných jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.  
  
 Tato metoda není bezpečná pro souběžnost s ohledem na dalších metodách, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_lt"></a>  operátor&lt; – operátor  
 Testuje, zda `concurrent_vector` objekt na levé straně operátoru menší než `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků uložených v souběžné vektorů.  
  
*A1*<br/>
Typ alokátoru prvního `concurrent_vector` objektu.  
  
*A2*<br/>
Typ alokátoru druhého `concurrent_vector` objektu.  
  
*_A*<br/>
Objekt typu `concurrent_vector`.  
  
*_B*<br/>
Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je souběžného vektoru na levé straně operátoru menší než souběžného vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je ekvivalentní operátor pro stejné jako `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná pro souběžnost s ohledem na dalších metodách, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_lt_eq"></a>  operátor&lt;= – operátor  
 Testuje, zda `concurrent_vector` je objekt na levé straně operátoru menší než nebo rovna hodnotě `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků uložených v souběžné vektorů.  
  
*A1*<br/>
Typ alokátoru prvního `concurrent_vector` objektu.  
  
*A2*<br/>
Typ alokátoru druhého `concurrent_vector` objektu.  
  
*_A*<br/>
Objekt typu `concurrent_vector`.  
  
*_B*<br/>
Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je souběžného vektoru na levé straně operátoru menší než nebo rovno souběžného vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je ekvivalentní operátor pro stejné jako `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná pro souběžnost s ohledem na dalších metodách, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_gt"></a>  operátor&gt; – operátor  
 Testuje, zda `concurrent_vector` je objekt na levé straně operátoru větší než `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků uložených v souběžné vektorů.  
  
*A1*<br/>
Typ alokátoru prvního `concurrent_vector` objektu.  
  
*A2*<br/>
Typ alokátoru druhého `concurrent_vector` objektu.  
  
*_A*<br/>
Objekt typu `concurrent_vector`.  
  
*_B*<br/>
Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je souběžného vektoru na levé straně operátoru větší než souběžného vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je ekvivalentní operátor pro stejné jako `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná pro souběžnost s ohledem na dalších metodách, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
##  <a name="operator_gt_eq"></a>  operátor&gt;= – operátor  
 Testuje, zda `concurrent_vector` je objekt na levé straně operátoru větší než nebo rovna hodnotě `concurrent_vector` objekt na pravé straně.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků uložených v souběžné vektorů.  
  
*A1*<br/>
Typ alokátoru prvního `concurrent_vector` objektu.  
  
*A2*<br/>
Typ alokátoru druhého `concurrent_vector` objektu.  
  
*_A*<br/>
Objekt typu `concurrent_vector`.  
  
*_B*<br/>
Objekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je souběžného vektoru na levé straně operátoru větší než nebo rovna hodnotě souběžného vektoru na pravé straně operátoru; v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Chování tohoto operátoru je ekvivalentní operátor pro stejné jako `vector` třídy v `std` oboru názvů.  
  
 Tato metoda není bezpečná pro souběžnost s ohledem na dalších metodách, které může změnit buď souběžných vektorů `_A` nebo `_B`.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
