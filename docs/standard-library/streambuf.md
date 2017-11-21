---
title: "&lt;streambuf –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <streambuf>
dev_langs: C++
helpviewer_keywords: streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 19be7e9ce24003dd2c00ddb0f9d9a1f5e92a5363
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltstreambufgt"></a>&lt;streambuf –&gt;
Zahrnují standardní hlavičku iostreams \<streambuf – > definovat šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), což je základní operace iostreams třídy. Tuto hlavičku je obvykle zahrnuté pro vás jiným hlaviček iostreams; je potřeba jen zřídka ho zahrňte přímo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <streambuf>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[streambuf –](../standard-library/streambuf-typedefs.md#streambuf)|Specializace z `basic_streambuf` používající `char` jako parametry šablony.|  
|[wstreambuf –](../standard-library/streambuf-typedefs.md#wstreambuf)|Specializace z `basic_streambuf` používající `wchar_t` jako parametry šablony.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_streambuf – třída](http://msdn.microsoft.com/en-us/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|Šablony třídy popisuje abstraktní základní třídu pro odvození datového proudu vyrovnávací paměti řídí přenos elementů do a z konkrétní reprezentace datového proudu.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



