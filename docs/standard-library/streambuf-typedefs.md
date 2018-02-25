---
title: "&lt;streambuf –&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 4abaa093b4fa739602e308ec420299907f4ded3f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf –&gt; – definice TypeDef
|||  
|-|-|  
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|  
  
##  <a name="streambuf"></a>  streambuf –  
 Specializace z `basic_streambuf` používající `char` jako parametry šablony.  
  
```
typedef basic_streambuf<char, char_traits<char>> streambuf;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_streambuf](../standard-library/basic-streambuf-class.md), specializované pro elementy typu `char` s vlastnostmi výchozí znak.  
  
##  <a name="wstreambuf"></a>  wstreambuf –  
 Specializace z `basic_streambuf` používající `wchar_t` jako parametry šablony.  
  
```
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro třídu šablony [basic_streambuf](../standard-library/basic-streambuf-class.md), specializované pro elementy typu `wchar_t` s vlastnostmi výchozí znak.  
  
## <a name="see-also"></a>Viz také  
 [\<streambuf>](../standard-library/streambuf.md)



