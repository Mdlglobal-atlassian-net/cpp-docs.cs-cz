---
title: Hstringreference::hstringreference – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc88ea32d4384b36559a4a10da0a5975345bf0d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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