---
title: includelib – (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e10ab341dc4c90a26315ea5e30f03bc71e628b64
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603378"
---
# <a name="includelib-c"></a>includelib (C++)
Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ includelib(  
   name.idl  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *name.IDL*  
 Název souboru, který chcete zahrnout jako součást souboru generovaného IDL.  
  
## <a name="remarks"></a>Poznámky  
 **Includelib** C++ atribut vygeneruje soubor IDL nebo .h mají být zahrnuty v souboru IDL vygenerované po `importlib` příkazu.  
  
## <a name="example"></a>Příklad  
 Následující kód můžete vidět v souboru s příponou .cpp:  
  
```cpp  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Kdekoli|  
|**Opakovatelné**|Ano|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl –](../windows/importidl.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   