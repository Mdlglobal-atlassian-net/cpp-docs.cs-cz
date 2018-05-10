---
title: importlib – | Microsoft Docs
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
ms.openlocfilehash: c21b97e50fa03861245a0c0881963387dd8a3102
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="importlib"></a>importlib
Díky typy, které již byly kompilovány do jiného typu knihovny k dispozici pro knihovny typů vytváří.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *tlb_file*  
 Název souboru .tlb, v uvozovkách, které chcete importované do knihovny typů aktuálního projektu.  
  
## <a name="remarks"></a>Poznámky  
 **Importlib –** C++ atributu způsobí, že `importlib` příkaz, který má být umístěn v bloku knihovny generovaného .idl souboru. **Importlib –** atribut má stejné funkce jako [importlib –](http://msdn.microsoft.com/library/windows/desktop/aa367050) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje příklad použití **importlib –**:  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl –](../windows/importidl.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [includelib –](../windows/includelib-cpp.md)