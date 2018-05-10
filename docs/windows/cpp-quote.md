---
title: cpp_quote – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38ecabcde55f49687abf7caff66fb2c316fab0fe
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="cppquote"></a>cpp_quote
Do souboru generovaného .idl vysílá zadaný řetězec bez znaky uvozovek za sebou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Příkaz*  
 Instrukce C.  
  
## <a name="remarks"></a>Poznámky  
 **Cpp_quote –** C++ atribut je užitečné, pokud je chcete umístit preprocesoru direktivě v souboru IDL.  
  
 Můžete také použít **cpp_quote –** a generovat soubor .h jako součást MIDL kompilace. Například pokud máte soubor hlaviček C++, který používá C++ IDL – atributy, ale tento soubor nelze použít pro některé úlohy, potom ji můžete zkompilovat k vytvoření souboru MIDL generovaný .h, které by měly být možné používat.  
  
 **Cpp_quote –** atribut má stejné funkce jako [cpp_quote –](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [duální](../windows/dual.md) příklad použití použití **cpp_quote –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
