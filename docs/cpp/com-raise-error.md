---
title: _com_raise_error | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54cb2183bccc45446cd68b8d5d6d2753f571009b
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408086"
---
# <a name="comraiseerror"></a>_com_raise_error
**Specifické pro Microsoft**  
  
 Vyvolá výjimku [_com_error](../cpp/com-error-class.md) v reakci na selhání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hr*  
 Informace o HRESULT.  
  
 *perrinfo*  
 `IErrorInfo` objekt.  
  
## <a name="remarks"></a>Poznámky  
 **_com_raise_error**, který je definován v \<comdef.h >, lze nahradit uživatelem zapsaný verze stejný název a vytváření prototypů. To může provést, pokud chcete použít `#import` , ale nechcete použít zpracování výjimek jazyka C++. V takovém případě uživatel verzi **_com_raise_error** může rozhodnout provést `longjmp` nebo zobrazení okna se zprávou a zastavit. Uživatel verze by neměly vracet, protože kód podpory kompilátoru modelu COM, který to vrátit neočekává.  
  
 Můžete také použít [_set_com_error_handler –](../cpp/set-com-error-handler.md) nahradit výchozí funkce zpracování chyb.  
  
 Ve výchozím nastavení **_com_raise_error** je definovaná následujícím způsobem:  
  
```cpp  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**Specifické pro END Microsoft**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<comdef.h >  
  
 **Lib:** Pokud **wchar_t je nativní typ** – možnost kompilátoru je na, použijte comsuppw.lib nebo comsuppwd.lib. Pokud **wchar_t je nativní typ** je, použijte comsupp.lib. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Viz také:  
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)