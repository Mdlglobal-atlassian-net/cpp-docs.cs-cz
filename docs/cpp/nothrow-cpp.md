---
title: nothrow (C++) | Microsoft Docs
ms.custom: ''
ms.date: 01/03/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nothrow_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69a706577cf112c3d8a3b7748f72679f7213936d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420647"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Konkrétní Microsoft**

Rozšířený atribut `__declspec`, který lze použít v deklaracích funkcí.

## <a name="syntax"></a>Syntaxe  
  
> *Návratový typ* __declspec(nothrow) [*konvence volání*] *název funkce* ([*seznam argumentů*])

## <a name="remarks"></a>Poznámky

Doporučujeme použít všechny nový kód [noexcept](noexcept-cpp.md) operátor místo `__declspec(nothrow)`.

Tento atribut oznamuje kompilátoru, že deklarovaná funkce a funkce, které volá, nikdy nevyvolají výjimku. Nevynucuje však direktivu. Jinými slovy, nikdy způsobuje [std::terminate](../standard-library/exception-functions.md#terminate) má být volána, na rozdíl od `noexcept`, nebo v **std:c ++ 17** režimu (Visual Studio 2017 verze 15,5 a novější), `throw()`.

V modelu synchronního zpracování výjimek, který je nyní výchozí, může kompilátor odstranit mechanismus sledování životnosti určitých nerozvinutelných objektů v takové funkci a významně tak snížit velikost kódu. Zadané následující direktivy preprocesoru, jsou následující tři funkce deklarace ekvivalentní v **/std: c ++ 14** režimu:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

V **/std: c ++ 17** režimu `throw()` není ekvivalentní ostatním, které používají `__declspec(nothrow)` protože způsobuje, že `std::terminate` má být volána, pokud je vyvolána výjimka z funkce.

`void __stdcall f3() throw();` Deklarace používá syntaxi definované C++ standard. Součástí C ++ 17 `throw()` – klíčové slovo se považovat za zastaralou.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)  
[noexcept](noexcept-cpp.md)  
[Klíčová slova](../cpp/keywords-cpp.md)  
