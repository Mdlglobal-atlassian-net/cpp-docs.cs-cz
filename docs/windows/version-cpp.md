---
title: verze (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db6c31df932890799f68e2ae466b0a927f0f999f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="version-c"></a>version (C++)
Identifikuje na konkrétní verzi mezi více verzí třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *verze*  
 Číslo verze coclass. Pokud není zadaný, 1.0 bude uložena v souboru IDL.  
  
## <a name="remarks"></a>Poznámky  
 **Verze** atribut C++ má stejné funkce jako [verze](http://msdn.microsoft.com/library/windows/desktop/aa367306) MIDL atribut a je předána do souboru generovaného IDL.  
  
## <a name="example"></a>Příklad  
 Najdete v článku [vazbu](../windows/bindable.md) příklad pro ukázkové použití **verze**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
