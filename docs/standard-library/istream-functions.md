---
title: '&lt;IStream on Request&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da4b05286c56bf809914b142a254a311f8655ce9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltistreamgt-functions"></a>&lt;IStream on Request&gt; funkce
|||  
|-|-|  
|[swap](#istream_swap)|[ws](#ws)|  
  
##  <a name="istream_swap"></a>swap  
 Výměny elementy dva objekty datového proudu.  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_istream<Elem, Tr>& left,  
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>  
void swap(
    basic_iostream<Elem, Tr>& left,  
    basic_iostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Datový proud.  
  
 `right`  
 Datový proud.  
  
##  <a name="ws"></a>ws  
 Přeskočí mezer v datovém proudu.  
  
```  
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```  
  
### <a name="parameters"></a>Parametry  
 `_Istr`  
 Datový proud.  
  
### <a name="return-value"></a>Návratová hodnota  
 Datový proud.  
  
### <a name="remarks"></a>Poznámky  
 Manipulator extrahuje a zahodí všechny elementy `ch` pro kterou [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**>> ( [getloc –](../standard-library/ios-base-class.md#getloc)). **je**( **ctype** \< **Elem**>:: **místo**, **ch**) hodnotu true.  
  
 Volání funkcí [setstate –](../standard-library/basic-ios-class.md#setstate)( **eofbit**) v případě nalezení konec souboru při extrahování elementy. Vrátí `_Istr`.  
  
### <a name="example"></a>Příklad  
  V tématu [operátor >>](../standard-library/istream-operators.md#op_gt_gt) příklad použití `ws`.  
  
## <a name="see-also"></a>Viz také  
 [\<IStream on Request >](../standard-library/istream.md)
