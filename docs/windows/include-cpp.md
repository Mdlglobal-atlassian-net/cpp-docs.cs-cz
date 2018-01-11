---
title: Zahrnout (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.include
dev_langs: C++
helpviewer_keywords: include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31d56b56b104473ffe3edbcf8672aa8b5a92243d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
