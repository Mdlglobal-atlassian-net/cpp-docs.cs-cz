---
title: vi_progid – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 687a8a70d7f0a5381160a6515c80f6940cc0a434
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891282"
---
# <a name="viprogid"></a>vi_progid
Určuje nezávislé na verzi forma identifikátor ProgID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 ProgID nezávislé na verzi, reprezentující objekt.  
  
 ProgID prezentovat čitelná pro člověka verzi identifikátor třídy (CLSID) použije k identifikaci objektů COM/ActiveX.  
  
## <a name="remarks"></a>Poznámky  
 **Vi_progid –** C++ atribut umožňuje určit ProgID nezávislé na verzi pro objekt COM. ProgID má tvar *name1.name2.version*. Nezávislé na verzi ProgID nemá *verze*. Je možné zadat oba seznamy **progid** a **vi_progid –** atributů na coclass. Pokud nezadáte **vi_progid –**, je nezávislý na verzi ProgID hodnotu zadanou pomocí [progid](../windows/progid.md) atribut.  
  
 **vi_progid –** znamená **třída typu coclass** atribut, který je zadáte-li **vi_progid –**, je totéž jako zadání **třída typu coclass** a **vi_progid –** atributy.  
  
 **Vi_progid –** atribut způsobuje třídu automaticky zaregistrovat se zadaným názvem. Soubor generovaný .idl nezobrazí ProgID hodnotu.  
  
 V projekty knihovny ATL Pokud [třída typu coclass](../windows/coclass.md) atribut také přítomen, zadaný ProgID používá **GetVersionIndependentProgID** funkce (vložená **třída typu coclass** atribut).  
  
## <a name="example"></a>Příklad  
 Najdete v článku [třída typu coclass](../windows/coclass.md) příklad pro ukázkové použití **vi_progid –**.  
  
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
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Klíč progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
