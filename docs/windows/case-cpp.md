---
title: případ (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30d665861688054a4f6b7491f449014afe646c71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860954"
---
# <a name="case-c"></a>case (C++)
Použít s [switch_type –](../windows/switch-type.md) atribut **sjednocení**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *value*  
 Možné vstupní hodnota, pro které byste chtěli poskytnout zpracování. Typ **hodnota** může být jedna z následujících typů:  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 nebo identifikátor takového typu.  
  
## <a name="remarks"></a>Poznámky  
 **Případ** atribut C++ má stejné funkce jako **případ** MIDL atribut. Tento atribut se používá pouze pro [switch_type –](../windows/switch-type.md) atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje k využívání **případ** atribut:  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Člen **třídy** nebo `struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
