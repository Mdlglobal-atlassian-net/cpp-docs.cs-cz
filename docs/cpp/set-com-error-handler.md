---
title: "_set_com_error_handler – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 52258c64c98651fc7a962c2a246fe8bde79d8ab8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler
**Konkrétní Microsoft**  
  
 Nahradí výchozí funkci, která se používá pro zpracování chyb modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHandler`  
 Ukazatel na náhradní funkci.  
  
 `hr`  
 Informace `HRESULT`.  
  
 `perrinfo`  
 `IErrorInfo`objekt.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení [_com_raise_error –](../cpp/com-raise-error.md) zpracovává všechny chyby COM. Toto chování lze změnit pomocí funkce `_set_com_error_handler` k volání vlastní funkce zpracování chyb.  
  
 Náhradní funkce musí mít podpis, který je ekvivalentní s funkcí `_com_raise_error`.  
  
## <a name="example"></a>Příklad  
  
```  
// _set_com_error_handler.cpp  
// compile with /EHsc  
#include <stdio.h>  
#include <comdef.h>  
#include <comutil.h>  
  
// Importing ado dll to attempt to establish an ado connection.  
// Not related to _set_com_error_handler   
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")  
  
void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)  
{  
   throw "Unable to establish the connection!";  
}  
  
int main()  
{  
   _set_com_error_handler(_My_com_raise_error);  
   _bstr_t bstrEmpty(L"");  
   _ConnectionPtr Connection = NULL;  
   try  
   {  
      Connection.CreateInstance(__uuidof(Connection));  
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);   
   }  
   catch(char* errorMessage)  
   {  
      printf("Exception raised: %s\n", errorMessage);  
   }  
  
   return 0;  
}  
```  
  
```Output  
Exception raised: Unable to establish the connection!  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comdef.h  
  
 **Lib:** Pokud **wchar_t je nativní typ** – možnost kompilátoru zapnutý, použijte comsuppw.lib nebo comsuppwd.lib. Pokud **wchar_t je nativní typ** je vypnuto, použijte comsupp.lib. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)