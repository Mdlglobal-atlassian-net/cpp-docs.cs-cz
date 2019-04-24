---
title: noexcept (C++)
ms.date: 01/12/2018
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: c314b554abb6c10e62b143f554777af50267e4e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245358"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++11:** Určuje, zda může funkce vyvolat výjimky.

## <a name="syntax"></a>Syntaxe

> *noexcept: výraz*: &nbsp; &nbsp; &nbsp; &nbsp; **noexcept** &nbsp; &nbsp; &nbsp; &nbsp; **noexcept (** *konstantní výraz* **)**

### <a name="parameters"></a>Parametry

*constant-expression*<br/>
Konstantní výraz typu **bool** , která uvádí, zda se sada možných typů výjimek byla prázdná. Nepodmíněný verze je ekvivalentní `noexcept(true)`.

## <a name="remarks"></a>Poznámky

A *noexcept výraz* je typ z *specifikace výjimky*, příponu k deklaraci funkce, která představuje sadu typů, které mohou odpovídat podvýrazu obslužné rutiny výjimky pro jakoukoliv výjimku, která ukončí funkce. Podmíněný operátor unární `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds **true**a jeho Nepodmíněný synonym **noexcept**, určuje, že sadu potenciální typy výjimek, které můžete ukončit funkci je prázdný. To znamená funkce vyvolá výjimku, nikdy a nikdy umožňuje výjimku mohly rozšířit mimo svůj rozsah. Operátor `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds **false**, nebo neexistenci specifikaci výjimky (jiné než funkce destruktoru nebo zrušení přidělení), znamená, že sadu potenciální výjimky, které můžete ukončit funkci je sada všech typů.

Označit funkce jako **noexcept** pouze v případě, že všechny funkce, které volá, buď přímo nebo nepřímo, jsou také **noexcept** nebo **const**. Kompilátor nekontroluje nutně každá cesta kódu pro výjimky, které se může být až **noexcept** funkce. Pokud výjimku ukončit vnějším oboru funkce označené `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) okamžitě, je vyvolána a neexistuje žádná záruka, že budou vyvolány destruktory všech objektů v oboru. Použití **noexcept** namísto specifikátoru dynamických výjimek `throw()`, který je nyní zastaralý ve standardu. Doporučujeme vám použít `noexcept` pro všechny funkce, které nikdy umožňuje výjimce šíření výše zásobníkem volání. Když je funkce deklarovaná **noexcept**, umožňuje kompilátoru generovat efektivnější kód v několika různých kontextech. Další informace najdete v tématu [specifikace výjimek](exception-specifications-throw-cpp.md).

## <a name="example"></a>Příklad

Funkce šablony, který kopíruje svůj argument může být deklarován **noexcept** za předpokladu, že objekt kopírování je prostý původní typ dat (POD). Takové funkce může být deklarována takto:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Viz také:

[Zpracovávání výjimek v jazyce C++](cpp-exception-handling.md)<br/>
[Specifikace výjimek (throw, noexcept)](exception-specifications-throw-cpp.md)