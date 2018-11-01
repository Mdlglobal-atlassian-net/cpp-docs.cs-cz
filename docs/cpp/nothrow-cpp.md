---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 88041b374cc48ac31c8990aa7f867ba25b33e1d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548132"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Specifické pro Microsoft**

A **__declspec** rozšířeného atributu, který lze použít v deklaracích funkcí.

## <a name="syntax"></a>Syntaxe

> *Návratový typ* __declspec(nothrow) [*konvence volání*] *název funkce* ([*seznam argumentů*])

## <a name="remarks"></a>Poznámky

Doporučujeme použít všechny nový kód [noexcept](noexcept-cpp.md) operátor spíše než `__declspec(nothrow)`.

Tento atribut oznamuje kompilátoru, že deklarovaná funkce a funkce, které volá, nikdy nevyvolají výjimku. Nevynucuje však směrnice. Jinými slovy, nikdy způsobí, že [std::terminate](../standard-library/exception-functions.md#terminate) má být volána, na rozdíl od `noexcept`, nebo v **std: c ++ 17** režimu (Visual Studio 2017 verze 15.5 nebo novější), `throw()`.

V modelu synchronního zpracování výjimek, který je nyní výchozí, může kompilátor odstranit mechanismus sledování životnosti určitých nerozvinutelných objektů v takové funkci a významně tak snížit velikost kódu. Zadaný direktivě preprocesoru, tři deklarace funkce níže jsou ekvivalentní ve **/std: c ++ 14** režimu:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

V **/std: c ++ 17** režimu `throw()` není ekvivalentní osobám, které používají `__declspec(nothrow)` protože kvůli němu `std::terminate` má být volána, pokud je výjimka vyvolána z funkce.

`void __stdcall f3() throw();` Deklarace používá syntaxi definované ve standardu jazyka C++. V C ++ 17 `throw()` – klíčové slovo se přestala nabízet.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)