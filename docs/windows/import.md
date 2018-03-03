---
title: Import | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 011cabb37f388d4be6a9a69f685a7c711f0209a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="import"></a>import
Určuje jiný .idl, .odl nebo hlavičce soubor obsahující definice, které chcete odkazovat z vaší hlavní IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 `idl_file`  
 Název souboru IDL, které chcete importované do knihovny typů aktuálního projektu.  
  
## <a name="remarks"></a>Poznámky  
 **Importovat** C++ atributu způsobí, že `#import` příkaz, který má být umístěny pod `import "docobj.idl"` příkaz v souboru generovaného IDL. **Importovat** atribut má stejné funkce jako [importovat](http://msdn.microsoft.com/library/windows/desktop/aa367047) MIDL atribut.  
  
 **Importovat** atribut pouze umístí zadaný soubor do souboru .idl generovaný projektu; **importovat** atribut neumožňuje volání konstrukce v zadaném souboru ze zdrojového kódu ve vašem projektu.  Chcete-li zavolat konstrukce v zadaném souboru zdrojového kódu v projektu, buď použijte [#import](../preprocessor/hash-import-directive-cpp.md) a `embedded_idl` atribut nebo je můžete zahrnout soubor .h pro `idl_file`, pokud existuje soubor h.  
  
## <a name="example"></a>Příklad  
 Následující kód:  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 vytváří následující kód v souboru generovaného .idl:  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
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
 [importidl –](../windows/importidl.md)   
 [importlib –](../windows/importlib.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [includelib –](../windows/includelib-cpp.md)   
