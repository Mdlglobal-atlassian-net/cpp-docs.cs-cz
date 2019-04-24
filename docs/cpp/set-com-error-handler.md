---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 864236e86b4aeb6ce7b3315df57af1b577693c26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267229"
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler

**Microsoft Specific**

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

**Header:** \<comdef.h>

**Lib:** Pokud **/Zc: wchar_t** je zadána možnost kompilátoru (výchozí), použijte comsuppw.lib nebo comsuppwd.lib. Pokud **/Zc:wchar_t-** – možnost kompilátoru je zadán, použijte knihovnu comsupp.lib. Další informace, včetně postupu nastavení této možnosti v integrovaném vývojovém prostředí, najdete v části [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Viz také:

[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)
