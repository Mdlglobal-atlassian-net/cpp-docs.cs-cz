---
title: nothrow (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 7efbd22c846327c5731cf3ab14ba1f2045c8636f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939146"
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

[__declspec](../cpp/declspec.md)  
[noexcept](noexcept-cpp.md)  
[Klíčová slova](../cpp/keywords-cpp.md)  
