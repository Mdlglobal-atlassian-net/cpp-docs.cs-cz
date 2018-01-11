---
title: "includelib – (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.includelib
dev_langs: C++
helpviewer_keywords: includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df6c38889db24cc1b4f28ce0bfe4cf96eb6b03a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="includelib-c"></a>includelib (C++)
Způsobí, že mají být zahrnuty v souboru generovaného .idl .idl nebo .h soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *name.IDL*  
 Název souboru .idl, který chcete součástí generovaného .idl souboru.  
  
## <a name="remarks"></a>Poznámky  
 `includelib` C++ atributu způsobí, že soubor .idl nebo .h mají být zahrnuty v souboru generovaného .idl po `importlib` příkaz.  
  
## <a name="example"></a>Příklad  
 Následující kód je zobrazena v souboru sada:  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ano|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl –](../windows/importidl.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
