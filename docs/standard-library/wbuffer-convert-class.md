---
title: "wbuffer_convert – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0153bf7d40dbd4290900d15b6e68d84d0c07869
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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
