---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: efb5ad272c8857e7a0dbd2c75885b826f2b8b9f8
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825361"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++ 11:** Určuje, zda funkce může vyvolat výjimky.

## <a name="syntax"></a>Syntaxe

> *s výjimkou výrazu*: \
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**\
> &nbsp;&nbsp;&nbsp;&nbsp;**s výjimkou (** *konstantní výraz* **)**

### <a name="parameters"></a>Parametry

*konstantní výraz*<br/>
Konstantní výraz typu **bool** , který představuje, zda je sada potenciálních typů výjimek prázdná. Nepodmíněný verze je ekvivalentem `noexcept(true)`.

## <a name="remarks"></a>Poznámky

*Výraz s výjimkou* je druh *specifikace výjimky*, přípona deklarace funkce, která představuje sadu typů, které mohou odpovídat obslužné rutině výjimky pro jakoukoliv výjimku, která ukončí funkci. Unární podmíněný operátor `noexcept(` *constant_expression* `)` , kde *constant_expression* vrací **true**a jeho nepodmíněné synonymum **s výjimkou**, určete, že sada potenciálních typů výjimek, které mohou opustit funkci, je prázdná. To znamená, že funkce nikdy nevyvolá výjimku a nikdy neumožňuje šířit výjimku mimo svůj rozsah. Operátor `noexcept(` *constant_expression* `)` , kde *constant_expression* vrací **hodnotu false**nebo absence specifikace výjimky (jiné než pro destruktor nebo unallocation), označuje, že sada potenciálních výjimek, které mohou opustit funkci, je sada všech typů.

Označte funkci jako **s výjimkou** pouze v případě, že všechny funkce, které volá, buď přímo, nebo nepřímo, jsou také **s výjimkou** nebo **const**. Kompilátor nemusí nutně kontrolovat každou cestu kódu pro výjimky, které by mohly být součástí funkce **s výjimkou** . Pokud výjimka ukončí vnější rozsah funkce označené `noexcept`, [std:: Terminate](../standard-library/exception-functions.md#terminate) je vyvolána okamžitě a neexistuje žádná záruka, že se vyvolají destruktory všech objektů v oboru. Použijte **výjimku s výjimkou** namísto dynamického specifikátoru `throw()`výjimky, který je nyní zastaralý ve standardu. Doporučujeme použít `noexcept` pro všechny funkce, které nikdy neumožňují výjimku pro rozšíření zásobníku volání. Je-li funkce deklarována **s výjimkou**, umožňuje kompilátoru generovat efektivnější kód v několika různých kontextech. Další informace naleznete v tématu [Specifikace výjimek](exception-specifications-throw-cpp.md).

## <a name="example"></a>Příklad

Funkce šablony, která kopíruje svůj argument, může být deklarována **s výjimkou** podmínky, že objekt, který je kopírován, je prostým starým datovým typem (pod). Taková funkce by mohla být deklarována takto:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Viz také

[Moderní osvědčené postupy jazyka C++ pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md)<br/>
[Specifikace výjimek (throw, s výjimkou)](exception-specifications-throw-cpp.md)
