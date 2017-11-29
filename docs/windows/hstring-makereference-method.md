---
title: "Hstring::makereference – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs: C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 026b036e3a4dad0fb88600cb64ac3da892eba2b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hstringmakereference-method"></a>HString::MakeReference – metoda
Vytvoří objekt HStringReference z parametr zadaný řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
#### <a name="parameters"></a>Parametry  
 `sizeDest`  
 Parametr šablony, který určuje velikost HStringReference cílové vyrovnávací paměti.  
  
 `str`  
 Odkaz na řetězec znaků celou.  
  
 `len`  
 Maximální délka `str` parametr vyrovnávací paměti pro použití v této operaci. Pokud `len` není zadán parametr, celý `str` parametr se používá.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt HStringReference, jehož hodnota je stejná jako zadaný `str` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)