---
title: library_block – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbd97897138edffba12baf47d64465b1f6ca0df4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="libraryblock"></a>library_block
Umístí konstrukce uvnitř bloku IDL knihovny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[library_block]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Při umístění konstrukce uvnitř bloku knihovny, je zajistit, že bude předána do knihovny typů, bez ohledu na to, jestli se odkazuje. Ve výchozím nastavení, upraveném pouze konstrukce [třída typu coclass](../windows/coclass.md), [dispinterface](../windows/dispinterface.md), a [idl_module –](../windows/idl-module.md) atributy jsou umístěny v bloku knihovny.  
  
## <a name="example"></a>Příklad  
 V následujícím kódu vlastní rozhraní je umístěn uvnitř bloku knihovny.  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
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
