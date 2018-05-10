---
title: idl_quote – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8844a4770d0a4746c9d9de32a593d0770dcc9a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="idlquote"></a>idl_quote
Umožňuje používat IDL konstrukce, které nejsou podporované v aktuální verzi Visual C++ a jejich předání do souboru generovaného IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Text*  
 Název atributu, který hodláte – kompilátor Visual C++ na předání do souboru generovaného IDL bez vrácení chybě kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Pokud **idl_quote –** C++ atribut slouží jako samostatné atribut (středníkem po pravá závorka), pak *text* je umístěn v souboru sloučené .idl, jako je. Pokud **idl_quote –** se používá na symbol, *text* se umístí do atribut blok pro tento symbol.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak můžete zadat nepodporovaného atributu (pomocí **v**, který je podporován) a postup definice a používání nedefinované .idl konstrukce:  
  
```  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 Tento kód způsobí, že MYFLOT a MYDUB a *text* položka umístit do generovaného .idl souboru. *Název* parametr vynutí *text* umístit před všechno, co odkazuje *název* v souboru generovaného .idl. *Závislosti* parametr vynutí definice seznamu závislostí umístit před *text* v souboru generovaného .idl.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
