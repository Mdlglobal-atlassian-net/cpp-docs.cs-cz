---
title: "&lt;ostream –&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: c9ab11cf6436888605a07c91051bf27c45e10fcf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream –&gt; – definice TypeDef
|||  
|-|-|  
|[ostream](#ostream)|[wostream](#wostream)|  
  
##  <a name="ostream"></a>  ostream –  
 Umožňuje vytvořit typ ze basic_ostream, který se specializuje na `char` a `char_traits` specializované na `char`.  
  
```
typedef basic_ostream<char, char_traits<char>> ostream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="wostream"></a>  wostream –  
 Umožňuje vytvořit typ ze basic_ostream, který se specializuje na `wchar_t` a `char_traits` specializované na `wchar_t`.  
  
```
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
## <a name="see-also"></a>Viz také  
 [\<ostream>](../standard-library/ostream.md)



