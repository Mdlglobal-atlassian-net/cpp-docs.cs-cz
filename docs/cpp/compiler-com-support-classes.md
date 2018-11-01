---
title: Třídy podpory kompilátoru modelu COM
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 066fe797bc500625e96e027777a70f278b88cddb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479661"
---
# <a name="compiler-com-support-classes"></a>Třídy podpory kompilátoru modelu COM

**Specifické pro Microsoft**

Standardní třídy se používá pro podporu některých typů modelu COM. Třídy jsou definovány v \<comdef.h > a souborech hlaviček generovaných z knihovny typů.

|Třída|Účel|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Zabalí `BSTR` typ poskytnout užitečné operátory a metody.|
|[_com_error](../cpp/com-error-class.md)|Definuje objekt chyby vyvolané [_com_raise_error](../cpp/com-raise-error.md) ve většině chyb.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Zapouzdřuje ukazatele rozhraní modelu COM a automatizuje vyžaduje volání `AddRef`, `Release`, a `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Zabalí `VARIANT` typ poskytnout užitečné operátory a metody.|

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Podpora kompilátoru COM](../cpp/compiler-com-support.md)<br/>
[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)