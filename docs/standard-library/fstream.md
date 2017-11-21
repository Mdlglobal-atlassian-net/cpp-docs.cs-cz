---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <fstream>
dev_langs: C++
helpviewer_keywords: fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc68979d4dc4b79a2b1e6e987f51bebc6d15aa3b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;
Definuje několik tříd, které podporují operace iostreams v pořadí, které jsou uložené v externích souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <fstream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specializované na `char` parametry šablony.|  
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specializované na `char` parametry šablony.|  
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specializované na `char` parametry šablony.|  
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specializované na `char` parametry šablony.|  
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specializované na `wchar_t` parametry šablony.|  
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specializované na `wchar_t` parametry šablony.|  
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specializované na `wchar_t` parametry šablony.|  
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specializované na `wchar_t` parametry šablony.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_filebuf –](../standard-library/basic-filebuf-class.md)|Šablony třídy popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**, do a z pořadí elementů uložená v externí soubor.|  
|[basic_fstream –](../standard-library/basic-fstream-class.md)|Šablony třídy popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**,  **Tr**>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**.|  
|[basic_ifstream –](../standard-library/basic-ifstream-class.md)|Šablony třídy popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**.|  
|[basic_ofstream –](../standard-library/basic-ofstream-class.md)|Šablony třídy popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, elementy typu **Elem**, jehož vlastnosti znak určuje třídu **Tr**.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



