---
title: importlib | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a4563d1b24b3af6e450a67a21d6a083f1839bc3e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603065"
---
# <a name="importlib"></a>importlib
Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ importlib(  
   "tlb_file"  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *tlb_file*  
 Název souboru .tlb v uvozovkách, které chcete importovat do knihovny typů aktuálního projektu.  
  
## <a name="remarks"></a>Poznámky  
 **Importlib** C++ atribut způsobí, že `importlib` příkaz umístit do bloku knihovny ze souboru generovaného IDL. **Importlib** atribut má stejné funkce jako [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje příklad, jak používat **importlib**:  
  
```cpp  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Kdekoli|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl –](../windows/importidl.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [includelib –](../windows/includelib-cpp.md)