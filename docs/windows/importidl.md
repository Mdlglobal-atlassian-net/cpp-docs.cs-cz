---
title: importidl – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5284c631813271f5682343c74cff693d1ea785e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877472"
---
# <a name="importidl"></a>importidl
Vloží zadaný .idl soubor do souboru generovaného IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ importidl(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 `idl_file`  
 Určuje název souboru .idl, který chcete sloučit s .idl soubor, který se budou generovat pro vaši aplikaci.  
  
## <a name="remarks"></a>Poznámky  
 **Importidl –** C++ atribut umístí části mimo knihovnu bloku (v `idl_file`) do vašeho programu generovaného .idl souboru a v části library (v `idl_file`) do části knihovny vašeho programu soubor generovaný .idl.  
  
 Můžete chtít použít **importidl –**, například, pokud chcete použít soubor programového ruční .idl s generovaného .idl souboru.  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [importlib –](../windows/importlib.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [includelib –](../windows/includelib-cpp.md)   
