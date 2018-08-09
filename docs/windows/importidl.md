---
title: importidl – | Dokumentace Microsoftu
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
ms.openlocfilehash: 1de680b2598a9439338986c283a4041482642fa0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015755"
---
# <a name="importidl"></a>importidl
Vloží zadaný souboru do generovaného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ importidl(  
   idl_file  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *idl_file*  
 Určuje název souboru, který chcete sloučit s souboru IDL se vygeneruje pro vaši aplikaci.  
  
## <a name="remarks"></a>Poznámky  
 **Importidl –** C++ atribut umístí části mimo blok knihovny (v *idl_file*) do generovaného souboru váš program a v části library (v *idl_file*) do knihovny část váš program vygeneruje soubor IDL.  
  
 Můžete chtít použít **importidl –**, například, pokud chcete použít soubor .idl. ruční pevně zakódované souborem generované IDL.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [importlib](../windows/importlib.md)   
 [Zahrnout](../windows/include-cpp.md)   
 [includelib –](../windows/includelib-cpp.md)   