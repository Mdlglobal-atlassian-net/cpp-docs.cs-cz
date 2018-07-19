---
title: Convertbstrtostring – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- ConvertBSTRToString
dev_langs:
- C++
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1278ab84ea8888b34290c9738e0eb88a4485e99c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947593"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString
**Specifické pro Microsoft**  
  
 Převede `BSTR` hodnota, která se **char \*** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
char* __stdcall ConvertBSTRToString(BSTR pSrc);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pSrc*  
 Proměnná BSTR.  
  
## <a name="remarks"></a>Poznámky  
 `ConvertBSTRToString` přidělí řetězec, který je potřeba odstranit.  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
**Specifické pro END Microsoft**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<comutil.h >.  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)  
  
## <a name="see-also"></a>Viz také  
 [Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)