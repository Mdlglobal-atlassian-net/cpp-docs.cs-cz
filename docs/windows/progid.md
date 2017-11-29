---
title: ProgID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.progid
dev_langs: C++
helpviewer_keywords: progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f7c0cdf844133cf64c3af70833caff7dc4cf275
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="progid"></a>progid
Určuje identifikátor ProgID pro objekt COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 ProgID reprezentující objekt.  
  
 ProgID prezentovat čitelná pro člověka verzi identifikátor třídy (CLSID) použije k identifikaci objektů COM/ActiveX.  
  
## <a name="remarks"></a>Poznámky  
 **Progid** C++ atribut umožňuje určit ProgID pro objekt COM. ProgID má tvar *name1.name2.version*. Pokud nezadáte *verze* pro ProgID, je výchozí verze 1. Pokud nezadáte *name1.name2*, výchozí název je *classname.classname*. Pokud nezadáte **progid** a zadáte **vi_progid –**, *name1.name2* jsou převzaty z **vi_progid –** a (Další sekvenčních verze Number) je připojen.  
  
 Pokud bloku atribut, který používá **progid** také nepoužívá `uuid`, kompilátor zkontroluje registru a zjistěte, zda `uuid` existuje pro zadaný **progid**. Pokud **progid** není zadán, verzi (a třída typu coclass název, pokud se vytváří třída typu coclass) se použije k vygenerování **progid**.  
  
 **ProgID** znamená **třída typu coclass** atribut, který je zadáte-li **progid**, je totéž jako zadání **třída typu coclass** a  **ProgID** atributy.  
  
 **Progid** atribut způsobuje třídu automaticky zaregistrovat se zadaným názvem. Soubor generovaný .idl nezobrazí **progid** hodnotu.  
  
 Pokud tento atribut se používá v rámci projekt, který používá ATL, změní chování atribut. Kromě výše uvedených chování informace zadaným tento atribut se používá v **GetProgID** funkce, vloženy **třída typu coclass** atribut. Další informace najdete v tématu [třída typu coclass](../windows/coclass.md) atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [třída typu coclass](../windows/coclass.md) pro ukázkové použití **progid**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Klíč progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   