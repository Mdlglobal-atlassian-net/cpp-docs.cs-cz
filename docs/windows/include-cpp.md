---
title: Zahrnout (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2c88dd610c1a0b8a8fee4e23da1b5ad844e989c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="include-c"></a>include (C++)
Určuje jeden nebo více soubory hlaviček, které mají být zahrnuty v souboru generovaného .idl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *HEADER_FILE*  
 Název souboru, který chcete součástí generovaného .idl souboru.  
  
## <a name="remarks"></a>Poznámky  
 **Zahrnují** C++ atributu způsobí, že `#include` příkaz, který má být umístěny pod `import "docobj.idl"` příkaz v souboru generovaného IDL.  
  
 **Zahrnují** atribut C++ má stejné funkce jako [zahrnují](http://msdn.microsoft.com/library/windows/desktop/aa367052) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje příklad použití **zahrnují**. V tomto příkladu include.h souboru obsahuje pouze #include příkaz.  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
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
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [Import](../windows/import.md)   
 [importidl –](../windows/importidl.md)   
 [includelib –](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
