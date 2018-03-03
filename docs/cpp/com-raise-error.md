---
title: "_com_raise_error – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71a4be4ebf6029d0573aee71d74bf9faa241319f
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="comraiseerror"></a>_com_raise_error
**Microsoft Specific**  
  
 Vyvolá [_com_error](../cpp/com-error-class.md) v reakci na selhání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 Informace `HRESULT`.  
  
 `perrinfo`  
 **IErrorInfo** objektu.  
  
## <a name="remarks"></a>Poznámky  
 `_com_raise_error`, která je definována v \<comdef.h >, lze nahradit uživatele zapsat verze se stejným názvem a prototypu. To může provést, pokud chcete použít `#import` , ale nechcete použít zpracovávání výjimek v jazyce C++. V takovém případě uživatel verzi **_com_raise_error –** rozhodnout uděláte `longjmp` nebo zobrazit okno se zprávou a zastavit. Verze uživatele by neměla vrátit, ale protože kód podpory kompilátoru modelu COM neočekává ho vrátit.  
  
 Můžete také použít [_set_com_error_handler –](../cpp/set-com-error-handler.md) nahradit výchozí chybovou funkci.  
  
 Ve výchozím nastavení `_com_raise_error` je definován následujícím způsobem:  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Header:** \<comdef.h>  
  
 **Lib:** Pokud **wchar_t je nativní typ** – možnost kompilátoru zapnutý, použijte comsuppw.lib nebo comsuppwd.lib. Pokud **wchar_t je nativní typ** je vypnuto, použijte comsupp.lib. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)