---
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 2065011ee6bbf98ce2c83be494f1e6631af9f7cf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170706"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Specifické pro společnost Microsoft**

Převede hodnotu `char *` na `BSTR`.

## <a name="syntax"></a>Syntaxe

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Proměnná `char *`.

## <a name="example"></a>Příklad

```cpp
// ConvertStringToBSTR.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")
#pragma comment(lib, "kernel32.lib")

int main() {
   char* lpszText = "Test";
   printf_s("char * text: %s\n", lpszText);

   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);
   wprintf_s(L"BSTR text: %s\n", bstrText);

   SysFreeString(bstrText);
}
```

```Output
char * text: Test
BSTR text: Test
```

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<comutil. h >

**Lib:** comsuppw. lib nebo comsuppwd. lib (viz [/Zc: Wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , kde najdete další informace.)

## <a name="see-also"></a>Viz také

[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)
