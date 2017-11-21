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
ms.openlocfilehash: 4091c8ae127077acbfe87d50a23a986d468d67ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [importlib –](../windows/importlib.md)   
