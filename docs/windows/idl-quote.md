---
title: idl_quote – | Dokumentace Microsoftu
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
ms.openlocfilehash: 96e316add17ff45425bd51a7e32b276b234c6906
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606511"
---
# <a name="idlquote"></a>idl_quote
Umožňuje použít IDL konstrukce, které nejsou podporovány v aktuální verzi jazyka Visual C++ a jejich předávání do souboru generovaného IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ idl_quote(  
   text  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Text*  
 Název atributu, který máte v úmyslu kompilátor Visual C++ pro převedení na generovaného souboru bez vrácení chybu kompilátoru.  
  
## <a name="remarks"></a>Poznámky  
 Pokud **idl_quote –** C++ atribut se používá jako samostatný atribut (oddělte středníkem. za uzavírací závorku), pak *text* je umístěn v souboru sloučeného IDL je. Pokud **idl_quote –** se používá na symbol, *text* je umístěn v rámci bloku atributu pro tento symbol.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak můžete zadat nepodporovaný atribut (pomocí **v**, které jsou podporovány) a jak definovat a používat nedefinované .idl konstrukce:  
  
```cpp  
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
  
 Tento kód způsobí, že MYFLOT a MYDUB a *text* položky budou umístěny v souboru generovaného IDL. *Název* vynutí parametr *text* umístit před cokoli, co odkazuje *název* v souboru generovaného IDL. *Závislosti* vynutí parametr definice seznamu závislostí umístit před *text* v souboru generovaného IDL.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Kdekoli|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   