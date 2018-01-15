---
title: "wbuffer_convert – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocmon/stdext::cvt::wbuffer_convert
dev_langs: C++
helpviewer_keywords: wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cee0951401c43cb72d58bf7e9e61e4f4a89d6675
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wbufferconvert-class"></a>wbuffer_convert – třída
Popisuje datový proud vyrovnávací paměť, která řídí přenos elementů do a z vyrovnávací paměti datového proudu bajtů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Codecvt`|[Národního prostředí](../standard-library/locale-class.md) omezující vlastnosti, který představuje objekt převod.|  
|`Elem`|Typ elementu široká charakterová.|  
|`Traits`|Vlastnosti související s *Elem*.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída šablony popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu `_Elem`, jejichž znak vlastnosti jsou popsány v třídě `Traits`, do a z vyrovnávací paměti datového proudu bajtů typu `std::streambuf`.  
  
 Převod mezi posloupnost `Elem` hodnoty a vícebajtové pořadí se provádí v objektu třídy `Codecvt<Elem, char, std::mbstate_t>`, který splňuje požadavky omezující vlastnost standardní převod kódu `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Tato třída šablony objektu ukládá:  
  
-   Ukazatel na jeho základní datový proud vyrovnávací paměť  
  
-   Ukazatel na objekt přidělené převodu (což je při vydání [wbuffer_convert](../standard-library/wbuffer-convert-class.md)
