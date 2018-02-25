---
title: "&lt;streambuf –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <streambuf>
dev_langs:
- C++
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0b6e565c3ec7b5ea7777125c400df775c65bb1d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;
Zahrnují standardní hlavičku iostreams \<streambuf – > definovat šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), což je základní operace iostreams třídy. Tuto hlavičku je obvykle zahrnuté pro vás jiným hlaviček iostreams; je potřeba jen zřídka ho zahrňte přímo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <streambuf>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specializace z `basic_streambuf` používající `char` jako parametry šablony.|  
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specializace z `basic_streambuf` používající `wchar_t` jako parametry šablony.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_streambuf – třída](http://msdn.microsoft.com/en-us/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|Šablony třídy popisuje abstraktní základní třídu pro odvození datového proudu vyrovnávací paměti řídí přenos elementů do a z konkrétní reprezentace datového proudu.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



