---
title: verze (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.version
dev_langs: C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 757ab7a6d2c8b846a51da359c4b8dc5a72c6e9e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|**Povinné atributy**|**Třída typu coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
