---
title: Třídy podpory kompilátoru modelu COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 1a9ff7c57965c9ba00881d5fe48501a6138b31d1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444433"
---
# <a name="compiler-com-support-classes"></a>Třídy podpory kompilátoru modelu COM

**Specifické pro společnost Microsoft**

Třídy Standard se používají k podpoře některých typů COM. Třídy jsou definovány ve \<Comdef. h > a hlavičkových souborech generovaných z knihovny typů.

|Třída|Účel|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Zabalí typ `BSTR`, aby poskytoval užitečné operátory a metody.|
|[_com_error](../cpp/com-error-class.md)|Definuje objekt Error vyvolaný [_com_raise_error](../cpp/com-raise-error.md) ve většině selhání.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Zapouzdřuje ukazatele rozhraní modelu COM a automatizuje požadovaná volání `AddRef`, `Release`a `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Zabalí typ `VARIANT`, aby poskytoval užitečné operátory a metody.|

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Podpora kompilátoru COM](../cpp/compiler-com-support.md)<br/>
[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)