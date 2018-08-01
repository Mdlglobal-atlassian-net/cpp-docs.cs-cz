---
title: _bstr_t – relační operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
dev_langs:
- C++
helpviewer_keywords:
- '>= operator [C++], comparing specific objects'
- operator<= [C++], bstr
- '!= operator'
- operator == [C++], bstr
- operator!= [C++], relational operators
- < operator [C++], comparing specific objects
- relational operators [C++], _bstr_t class
- operator== [C++], bstr
- <= operator [C++], with specific objects
- operator <= [C++], bstr
- operator >= [C++], bstr
- operator != [C++], relational operators
- '> operator [C++], comparing specific objects'
- operator< [C++], bstr
- == operator [C++], with specific Visual C++ objects
- operator>= [C++], bstr
- operator < [C++], bstr
- operator > [C++], bstr
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97595b29c2d79cd6209479e39987208cafe6f0f8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401779"
---
# <a name="bstrt-relational-operators"></a>_bstr_t – relační operátory
**Specifické pro Microsoft**  
  
 Porovná dva `_bstr_t` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool operator!( ) const throw( );   
bool operator==(const _bstr_t& str) const throw( );  
bool operator!=(const _bstr_t& str) const throw( );  
bool operator<(const _bstr_t& str) const throw( );  
bool operator>(const _bstr_t& str) const throw( );  
bool operator<=(const _bstr_t& str) const throw( );  
bool operator>=(const _bstr_t& str) const throw( );  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto operátory porovnávají dva objekty `_bstr_t` lexikograficky. Operátory vrací TRUE, pokud porovnání projdou, jinak vrátí FALSE.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_bstr_t – třída](../cpp/bstr-t-class.md)