---
title: REF (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.ref
dev_langs: C++
helpviewer_keywords: ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43c81346f7d92d75aade9b5cfc9ae845ce51c8f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ref-c"></a>ref (C++)
Identifikuje ukazatel odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[ref]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 `ref` Atribut C++ má stejné funkce jako [ref](http://msdn.microsoft.com/library/windows/desktop/aa367153) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití `ref` atribut:  
  
```  
// cpp_attr_ref_ref.cpp  
// compile with: /LD  
#include <windows.h>   
[module(name="ATLFIRELib")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );   
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`typedef`, rozhraní parametrů, metody rozhraní|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   