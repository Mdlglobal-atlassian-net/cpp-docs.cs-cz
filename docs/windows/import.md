---
title: Importovat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 529e6f3a8e2b30be38d80ec253d394077c9f7f0f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017094"
---
# <a name="import"></a>import
Určuje jiný soubor .idl, .odl nebo záhlaví obsahující definice, kterou chcete odkazovat z hlavní IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ import(  
   idl_file  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *idl_file*  
 Název souboru IDL, který chcete importovat do knihovny typů aktuálního projektu.  
  
## <a name="remarks"></a>Poznámky  
 **Importovat** C++ atribut způsobí, že `#import` příkaz umístit pod `import "docobj.idl"` příkaz v souboru generovaného IDL. **Importovat** atribut má stejné funkce jako [importovat](http://msdn.microsoft.com/library/windows/desktop/aa367047) atribut MIDL.  
  
 **Importovat** atribut pouze umístí do souboru IDL, který se vygeneruje vaším projektem; zadaný soubor **importovat** atribut neumožňuje volání konstruktorů v zadaném souboru ze zdrojového kódu ve vašem projektu.  Pokud chcete volat konstrukce v zadaném souboru ze zdrojového kódu ve vašem projektu, buď použijte [#import](../preprocessor/hash-import-directive-cpp.md) a `embedded_idl` atribut nebo je můžete zahrnout soubor hlaviček pro *idl_file*, pokud existuje soubor hlaviček.  
  
## <a name="example"></a>Příklad  
 Následující kód:  
  
```cpp  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 vytvoří následující kód v souboru generovaného IDL:  
  
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
|**Platí pro**|Kdekoli|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [importidl –](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [includelib –](../windows/includelib-cpp.md)   