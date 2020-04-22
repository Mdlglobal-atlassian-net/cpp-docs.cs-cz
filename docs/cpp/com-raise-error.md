---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745078"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Specifické pro Microsoft**

Vyvolá [_com_error](../cpp/com-error-class.md) v reakci na selhání.

## <a name="syntax"></a>Syntaxe

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parametry

*Hr*<br/>
Informace HRESULT.

*perrinfo*<br/>
`IErrorInfo`Objekt.

## <a name="remarks"></a>Poznámky

**_com_raise_error**, který \<je definován v> comdef.h, může být nahrazen uživatelem psanou verzí se stejným názvem a prototypem. To lze provést, pokud `#import` chcete použít, ale nechcete používat zpracování výjimek Jazyka C++. V takovém případě se **_com_raise_error** uživatelská verze _com_raise_error `longjmp` může rozhodnout provést nebo zobrazit okno se zprávou a zastavit. Uživatelská verze by se však neměla vrátit, protože kód podpory com kompilátoru neočekává, že se vrátí.

Můžete také použít [_set_com_error_handler](../cpp/set-com-error-handler.md) nahradit výchozí funkci zpracování chyb.

Ve výchozím nastavení je **_com_raise_error** definováno takto:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**END Microsoft Specifické**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<comdef.h>

**Lib:** Pokud je možnost kompilátoru **nativního typu wchar_t** zapnutá, použijte comsuppw.lib nebo comsuppwd.lib. Pokud **je wchar_t nativní typ** vypnutý, použijte comsupp.lib. Další informace naleznete v tématu [/Zc:wchar_t (wchar_t je nativní typ).](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>Viz také

[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
