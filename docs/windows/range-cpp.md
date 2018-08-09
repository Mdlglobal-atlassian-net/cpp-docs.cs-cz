---
title: rozsah (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.range
dev_langs:
- C++
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bf4f02043f3cb11a47357ff91898da23ed03c22
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014205"
---
# <a name="range-c"></a>range (C++)
Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ range(  
   low,   
   high  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Nízká*  
 Hodnota nízkého rozsahu.  
  
 *Vysoká*  
 Hodnota vysokého rozsahu.  
  
## <a name="remarks"></a>Poznámky  
 **Rozsah** C++ atribut má stejné funkce jako [rozsah](http://msdn.microsoft.com/library/windows/desktop/aa367151) atribut MIDL.  
  
## <a name="example"></a>Příklad  
  
```cpp  
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
|**Platí pro**|Metoda rozhraní parametr rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy datového členu](../windows/data-member-attributes.md)   