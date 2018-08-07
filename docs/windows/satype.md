---
title: satype – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a5376e0e830654c15dc31522b07ed53af4492bf
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603391"
---
# <a name="satype"></a>satype
Určuje datový typ `SAFEARRAY` struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ satype(  
   data_type  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *data_type*  
 Datový typ `SAFEARRAY` datová struktura, která je předána jako parametr metody rozhraní.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní parametrů, metody rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
## <a name="remarks"></a>Poznámky  
 **Satype –** C++ atribut určuje datový typ `SAFEARRAY`.  
  
> [!NOTE]
>  Z je vyřadit určitou úroveň dereference `SAFEARRAY` ukazatel v souboru IDL vygenerovaný v tom, jak je deklarován v souboru .cpp.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [id](../windows/id.md)   