---
title: "Výchozí (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.default
dev_langs: C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 352fca07ecb9528bb11ff1cb5cc1f701bfa01e1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="default-c"></a>default (C++)
Označuje, že vlastní a odesílající rozhraní definované v rámci coclass představuje výchozí programovatelnosti rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ default(  
   interface1,  
   interface2  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *interface1*  
 Výchozí rozhraní, která bude k dispozici do skriptovací prostředí, které vytvoření objektu na základě třídy definované pomocí **výchozí** atribut.  
  
 Pokud není zadán žádný výchozí rozhraní, první výskyt nonsource rozhraní se používá jako výchozí.  
  
 *interface2*(volitelné)  
 Výchozí zdroj rozhraní. Toto rozhraní se musíte zadat také [zdroj](../windows/source-cpp.md) atribut.  
  
 Pokud není zadán žádný výchozí zdroj rozhraní, první rozhraní zdroje se používá jako výchozí.  
  
## <a name="remarks"></a>Poznámky  
 **Výchozí** atribut C++ má stejné funkce jako [výchozí](http://msdn.microsoft.com/library/windows/desktop/aa366787) MIDL atribut. **Výchozí** atribut se také používá s [případ](../windows/case-cpp.md) atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak **výchozí** v definici coclass slouží k určení **ICustomDispatch** jako výchozí programovatelnosti rozhraní:  
  
```  
// cpp_attr_ref_default.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
  
[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]   
__interface IDual {  
   HRESULT Dual([in] long l, [out, retval] long *pLong);  
};  
  
[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustomDispatch : public IDispatch {  
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);  
};  
  
[   coclass,  
   default(ICustomDispatch),   
   source(IDual),  
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]  
class CClass : public ICustom, public IDual, public ICustomDispatch {  
   HRESULT Custom(long l, long *pLong) { return(S_OK); }  
   HRESULT Dual(long l, long *pLong) { return(S_OK); }  
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }  
};  
  
int main() {  
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch  
   CClass *pClass = new CClass;  
  
   long llong;  
  
   pClass->custom(1, &llong);  
   pClass->dual(1, &llong);  
   pClass->dispinterface(1, &llong);  
   pClass->dispatch(1, &llong);  
  
   delete pClass;  
#endif  
   return(0);  
}  
```  
  
 [Zdroj](../windows/source-cpp.md) atribut obsahuje také příklad použití **výchozí**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`, – datový člen|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass** (při použití **třída** nebo `struct`)|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Třída typu coclass](../windows/coclass.md)   
