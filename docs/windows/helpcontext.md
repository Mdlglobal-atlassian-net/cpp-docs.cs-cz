---
title: HelpContext – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 317e204c7292c4a7cccb1f81f6bc9d2a2fbfd407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="helpcontext"></a>helpcontext
Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 ID kontextu tématu nápovědy. V tématu [nápovědy HTML: Context-Sensitive Nápověda pro vaše programy](../mfc/html-help-context-sensitive-help-for-your-programs.md) Další informace o kontextu ID.  
  
## <a name="remarks"></a>Poznámky  
 **HelpContext –** atribut C++ má stejné funkce jako [HelpContext –](http://msdn.microsoft.com/library/windows/desktop/aa366851) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) příklad použití **HelpContext –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`, `typedef`, **třída**, metoda, vlastnost|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Soubor nápovědy](../windows/helpfile.md)   
 [helpstring](../windows/helpstring.md)   
