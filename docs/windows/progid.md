---
title: ProgID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b2d2168b568c74c5404cc83bab1e5f77570773
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880430"
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
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Klíč progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
