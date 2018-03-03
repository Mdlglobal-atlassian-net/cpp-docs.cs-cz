---
title: Export | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24619e3a0e707b40590b0ffb37b415629a18b1cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="export"></a>export
Způsobí, že datová struktura umístit do souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[export]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Exportovat** C++ atributu způsobí, že datová struktura umístit do souboru IDL a pak být k dispozici v knihovně typů kompatibilní binární formát, který je k dispozici pro použití s žádný jazyk.  
  
 Nelze použít **exportovat** atribut třídy i v případě, že třída má pouze veřejné členy (ekvivalent `struct`).  
  
 Pokud exportujete nepojmenované `enum`s nebo `struct`s, nebudou se zadaným názvy, které začínají **__unnamed***x*, kde *x* je pořadové číslo.  
  
 Platná pro export definice TypeDef jsou základní typy, struktury, sjednocení, výčty a zadejte identifikátory.  V tématu [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití **exportovat** atribut:  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**sjednocení**, `typedef`, `enum`, `struct`, nebo`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)   
