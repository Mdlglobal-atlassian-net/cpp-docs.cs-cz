---
title: "_com_raise_error – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_raise_error
dev_langs: C++
helpviewer_keywords: _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a7dc58ae5d50c59836dd6471b8118c37f739702
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comraiseerror"></a>_com_raise_error
**Konkrétní Microsoft**  
  
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
 `_com_raise_error`, která je definována v comdef.h, lze nahradit uživatele zapsat verze se stejným názvem a prototypu. To může provést, pokud chcete použít `#import` , ale nechcete použít zpracovávání výjimek v jazyce C++. V takovém případě uživatel verzi **_com_raise_error –** rozhodnout uděláte `longjmp` nebo zobrazit okno se zprávou a zastavit. Verze uživatele by neměla vrátit, ale protože kód podpory kompilátoru modelu COM neočekává ho vrátit.  
  
 Můžete také použít [_set_com_error_handler –](../cpp/set-com-error-handler.md) nahradit výchozí chybovou funkci.  
  
 Ve výchozím nastavení `_com_raise_error` je definován následujícím způsobem:  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comdef.h  
  
 **Lib:** Pokud **wchar_t je nativní typ** – možnost kompilátoru zapnutý, použijte comsuppw.lib nebo comsuppwd.lib. Pokud **wchar_t je nativní typ** je vypnuto, použijte comsupp.lib. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler –](../cpp/set-com-error-handler.md)