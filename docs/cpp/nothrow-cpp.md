---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8164f47190267627bdaf7c7ee2f03f22f65c8f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161058"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Specifické pro společnost Microsoft**

Rozšířený atribut **__declspec** , který lze použít v deklaraci funkce.

## <a name="syntax"></a>Syntaxe

> *návratový typ* __declspec (throw) [*Call-Convention*] *– název funkce* ([*seznam argumentů*])

## <a name="remarks"></a>Poznámky

Doporučujeme, aby všechny nové kódy používaly operátor [s výjimkou](noexcept-cpp.md) místo `__declspec(nothrow)`.

Tento atribut oznamuje kompilátoru, že deklarovaná funkce a funkce, které volá, nikdy nevyvolají výjimku. Neuplatňuje ale direktivu. Jinými slovy, nikdy nezpůsobí vyvolání [std:: Terminate](../standard-library/exception-functions.md#terminate) , na rozdíl od `noexcept`nebo v **std: c++ 17** mode (Visual Studio 2017 verze 15,5 a novější), `throw()`.

V modelu synchronního zpracování výjimek, který je nyní výchozí, může kompilátor odstranit mechanismus sledování životnosti určitých nerozvinutelných objektů v takové funkci a významně tak snížit velikost kódu. S ohledem na následující direktivy preprocesoru jsou tři deklarace funkcí níže ekvivalentní v **/std: režim c++ 14** :

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

V **/std: režim c++ 17** , `throw()` se neshoduje s jinými uživateli, kteří používají `__declspec(nothrow)`, protože to způsobuje, že `std::terminate` být vyvolány, pokud je vyvolána výjimka z funkce.

Deklarace `void __stdcall f3() throw();` používá syntaxi definovanou C++ standardem. V jazyce C++ 17 klíčové slovo `throw()` bylo Zastaralé.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
