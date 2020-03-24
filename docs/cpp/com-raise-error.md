---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 2012ec98d8d40d60a7f12feb68bdc371e1616223
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189790"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Specifické pro společnost Microsoft**

Vyvolá [_com_error](../cpp/com-error-class.md) jako odpověď na selhání.

## <a name="syntax"></a>Syntaxe

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parametry

*oddělení*<br/>
Informace HRESULT.

*perrinfo*<br/>
objekt `IErrorInfo`.

## <a name="remarks"></a>Poznámky

**_com_raise_error**, která je definována v \<Comdef. h >, může být nahrazena uživatelem vytvořenou verzí se stejným názvem a prototypem. To lze provést, pokud chcete použít `#import`, ale nechcete používat C++ zpracování výjimek. V takovém případě se může u uživatelské verze **_com_raise_error** rozhodnout `longjmp` nebo zobrazit okno se zprávou a zastavit. Verze uživatele by neměla vracet, ale protože kód podpory kompilátoru modelu COM neočekává, že se má vrátit.

Můžete také použít [_set_com_error_handler](../cpp/set-com-error-handler.md) k nahrazení výchozí funkce pro zpracování chyb.

Ve výchozím nastavení je **_com_raise_error** definováno následujícím způsobem:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<Comdef. h >

**Lib:** Pokud je **wchar_t možnost kompilátoru nativní typ** , použijte comsuppw. lib nebo comsuppwd. lib. Pokud je **nativní typ wchar_t** vypnutý, použijte knihovnu comsupp. lib. Další informace naleznete v tématu [/Zc: wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Viz také

[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
