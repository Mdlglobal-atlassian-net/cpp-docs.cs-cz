---
title: "&lt;IStream on Request&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 866950a000556392a9c44122c32775e0f9d59422
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltistreamgt-typedefs"></a>&lt;IStream on Request&gt; – definice TypeDef
||||  
|-|-|-|  
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|  
|[wistream](#wistream)|  
  
##  <a name="iostream">iostream</a>  
 Typ `basic_iostream` specializované na `char`.  
  
```  
typedef basic_iostream<char, char_traits<char>> iostream;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_iostream](../standard-library/basic-iostream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="istream"></a>  IStream on Request  
 Typ `basic_istream` specializované na `char`.  
  
```  
typedef basic_istream<char, char_traits<char>> istream;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_istream](../standard-library/basic-istream-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="wiostream"></a>  wiostream  
 Typ `basic_iostream` specializované na `wchar_t`.  
  
```  
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_iostream](../standard-library/basic-iostream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
##  <a name="wistream"></a>  wistream  
 Typ `basic_istream` specializované na `wchar_t`.  
  
```  
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_istream](../standard-library/basic-istream-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
## <a name="see-also"></a>Viz také  
 [\<istream>](../standard-library/istream.md)

