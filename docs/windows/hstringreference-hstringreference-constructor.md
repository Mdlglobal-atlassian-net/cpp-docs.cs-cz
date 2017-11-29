---
title: "Hstringreference::hstringreference – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs: C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b73e25977b91940031316f6d85c0bcfded4ab3ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference – konstruktor
Inicializuje novou instanci třídy HStringReference.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `sizeDest`  
 Parametr šablony, který určuje velikost HStringReference cílové vyrovnávací paměti.  
  
 `str`  
 Odkaz na řetězec znaků celou.  
  
 `len`  
 Maximální délka `str` parametr vyrovnávací paměti pro použití v této operaci. Pokud `len` není zadán parametr, celý `str` parametr se používá. Pokud `len` je větší než `sizeDest`, `len` je nastaven na `sizeDest`-1.  
  
 `other`  
 Jiný HStringReference objekt.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje nový objekt HStringReference stejná velikost jako parametr `str`.  
  
 Druhý konstruktor inicializuje nové HStringReference objektu, který specifeid velikost parametrem `len`.  
  
 Třetí konstruktor inicializuje nový objekt HStringReference na hodnotu `other` parametr a pak zničí `other` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HStringReference – třída](../windows/hstringreference-class.md)