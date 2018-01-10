---
title: "&lt;ostream –&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ostream/std::operator&lt;&lt;
dev_langs: C++
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f78befe92263dd6b4ef666c865ef9dd65c7103db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltostreamgt-operators"></a>&lt;ostream –&gt; operátory
||  
|-|  
|[operátor&lt;&lt;](#op_lt_lt)|  
  
##  <a name="op_lt_lt"></a>operátor&lt;&lt;  
 Různé typy zapíše do datového proudu.  
  
```
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
 `_Elem`  
 Typ elementu.  
  
 `_Ostr`  
 A `basic_ostream` objektu.  
  
 `str`  
 Řetězec znaků.  
  
 `_Tr`  
 Vlastnosti znak.  
  
 `val`  
 Typ  
  
### <a name="return-value"></a>Návratová hodnota  
 Datový proud.  
  
### <a name="remarks"></a>Poznámky  
 `basic_ostream` Třída také definuje několik operátorů insertion. Další informace najdete v tématu [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).  
  
 Funkce šablony  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```  
  
 Určuje délku N = `traits_type::` [délka](../standard-library/char-traits-struct.md#length)( `str`) z pořadí počínaje `str`a vloží sekvenci. Pokud N < `_Ostr.` [šířka](../standard-library/ios-base-class.md#width), potom funkce také vloží opakování `_Ostr.width` -N výplně znaků. Opakování předchází sekvenci, pokud ( `_Ostr`. [příznaky](../standard-library/ios-base-class.md#flags)  &  `adjustfield` ! = [levém](../standard-library/ios-functions.md#left). Opakování, jinak hodnota odpovídá pořadí. Funkce vrátí hodnotu `_Ostr`.  
  
 Funkce šablony  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 Vloží element `_Ch`. Je-li 1 < `_Ostr.width`, potom funkce také vloží opakování `_Ostr.width` – 1 vyplnění znaků. Opakování předchází sekvenci, pokud `_Ostr.flags & adjustfield != left`. Opakování, jinak hodnota odpovídá pořadí. Vrátí `_Ostr`.  
  
 Funkce šablony  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```  
  
 se chová stejně jako  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```  
  
 Kromě toho, že každý prvek `_Ch` z pořadí počínaje `str` je převést na objekt typu `Elem` voláním `_Ostr.` [put](../standard-library/basic-ostream-class.md#put)( `_Ostr.` [widen](../standard-library/basic-ios-class.md#widen)( `_Ch`)).  
  
 Funkce šablony  
  
```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```  
  
 se chová stejně jako  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 Kromě toho, že `_Ch` je převést na objekt typu `Elem` voláním `_Ostr.put`( `_Ostr.widen`( `_Ch`)).  
  
 Funkce šablony  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```  
  
 se chová stejně jako  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```  
  
 (Nemá rozšíří elementy ještě před jejich vložením.)  
  
 Funkce šablony  
  
```cpp  
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```  
  
 se chová stejně jako  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 (Chcete-li rozšířit nemá `_Ch` před vložením.)  
  
 Funkce šablony  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```  
  
 Vrátí `_Ostr` << ( `const char *`) `str`.  
  
 Funkce šablony  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```  
  
 Vrátí `_Ostr` << ( `char`) `_Ch`.  
  
 Funkce šablony:  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```  
  
 Vrátí `_Ostr` << ( `const char *`) `str`.  
  
 Funkce šablony:  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```  
  
 Vrátí `_Ostr` << ( `char`) `_Ch`.  
  
 Funkce šablony:  
  
```cpp  
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```  
  
 Vrátí `_Ostr` `<<` `val` (a převede [deklarátor odkazu hodnoty](../cpp/rvalue-reference-declarator-amp-amp.md) k `_Ostr` k lvalue v procesu).  
  
### <a name="example"></a>Příklad  
  V tématu [vyprázdnění](../standard-library/ostream-functions.md#flush) pro příklad použití `operator<<`.  
  
## <a name="see-also"></a>Viz také  
 [\<ostream – >](../standard-library/ostream.md)



