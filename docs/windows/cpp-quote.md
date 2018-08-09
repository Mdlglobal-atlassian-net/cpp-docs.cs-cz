---
title: cpp_quote – | Dokumentace Microsoftu
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
ms.openlocfilehash: 21f986e227e9daca58731d03c40d6dae5b0c0a80
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653037"
---
# <a name="cppquote"></a>cpp_quote
Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ cpp_quote(  
   "statement"  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *– Příkaz*  
 Instrukce C.  
  
## <a name="remarks"></a>Poznámky  
 **Cpp_quote –** C++ atribut je užitečné, pokud chcete umístit direktivy preprocesoru v souboru IDL.  
  
 Můžete také použít **cpp_quote –** a generování souboru .h jako část kompilace MIDL. Například pokud máte soubor hlaviček jazyka C++, která používá C++ IDL – atributy, ale tento soubor nelze použít pro některé úlohy, pak ji můžete zkompilovat vytvořit generované MIDL. h: soubor, který byste měli použít.  
  
 **Cpp_quote –** atribut má stejné funkce jako [cpp_quote –](http://msdn.microsoft.com/library/windows/desktop/aa366765) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [duální](../windows/dual.md) příklad použití použití **cpp_quote –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Kdekoli|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   