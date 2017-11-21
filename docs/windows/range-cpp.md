---
title: rozsah (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.range
dev_langs: C++
helpviewer_keywords: range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a43ad22484ec8502c66c16caa40933bf8f422df9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="range-c"></a>range (C++)
Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastaveny v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ range(  
   low,   
   high  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *nízkou*  
 Hodnota nízkou rozsahu.  
  
 *Vysoká*  
 Hodnota vysoká rozsahu.  
  
## <a name="remarks"></a>Poznámky  
 **Rozsah** atribut C++ má stejné funkce jako [rozsah](http://msdn.microsoft.com/library/windows/desktop/aa367151) MIDL atribut.  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Metody rozhraní, parametr rozhraní|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy datového členu](../windows/data-member-attributes.md)   
