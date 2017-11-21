---
title: "Convertbstrtostring – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ConvertBSTRToString
dev_langs: C++
helpviewer_keywords: ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db0a8cafbc48e4153092475026fad245d94f8e00
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString
**Konkrétní Microsoft**  
  
 Převede `BSTR` hodnotu **char \*** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      char* __stdcall ConvertBSTRToString(  
   BSTR pSrc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSrc`  
 BSTR proměnné.  
  
## <a name="remarks"></a>Poznámky  
 `ConvertBSTRToString`přiděluje řetězec, který je nutné odstranit.  
  
## <a name="example"></a>Příklad  
  
```  
// ConvertBSTRToString.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
  
int main() {  
   BSTR bstrText = ::SysAllocString(L"Test");  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);  
   printf_s("char * text: %s\n", lpszText2);  
  
   SysFreeString(bstrText);  
   delete[] lpszText2;  
}  
```  
  
```Output  
BSTR text: Test  
char * text: Test  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comutil.h.  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)