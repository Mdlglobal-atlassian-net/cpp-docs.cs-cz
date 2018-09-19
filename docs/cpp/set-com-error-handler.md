---
title: _set_com_error_handler – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 192707fe15560adb816b530ecf0e67713ae7d302
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092554"
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler

**Specifické pro Microsoft**

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

*pHandler*<br/>
Ukazatel na náhradní funkci.

*hr*<br/>
Informace o HRESULT.

*perrinfo*<br/>
`IErrorInfo` objekt.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení [_com_raise_error](../cpp/com-raise-error.md) zpracovává všechny chyby modelu COM. Toto chování můžete změnit pomocí **_set_com_error_handler –** k volání vlastní funkce zpracování chyb.

Náhradní funkce musí mít podpis, který je ekvivalentní s funkcí `_com_raise_error`.

## <a name="example"></a>Příklad

```cpp
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

**Záhlaví:** \<comdef.h >

**Lib:** Pokud **wchar_t je nativní typ** – možnost kompilátoru je na, použijte comsuppw.lib nebo comsuppwd.lib. Pokud **wchar_t je nativní typ** je, použijte comsupp.lib. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Viz také:

[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)