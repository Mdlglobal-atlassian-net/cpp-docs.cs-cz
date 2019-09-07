---
title: Atributy (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 77962dc2d4b7f6bda90a5376e5154782365a4106
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740378"
---
# <a name="attributes-ccx"></a>Atributy (C++/CX)

Atribut je zvláštní druh referenční třídy, který může být uzavřen do hranatých závorek, aby prostředí Windows Runtime typy a metody, které určují určité chování při vytváření metadat. Několik předdefinovaných atributů – například [Windows:: Foundation:: metadata:: WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)– se běžně používají v C++kódu/CX. Tento příklad ukazuje, jak je atribut použit pro třídu:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Vlastní atributy

Můžete také definovat vlastní atributy. Vlastní atributy musí splňovat následující pravidla prostředí Windows Runtime:

- Vlastní atributy můžou obsahovat jenom veřejná pole.

- Vlastní pole atributu lze inicializovat při použití atributu na třídu.

- Pole může být jedním z těchto typů:

   - Int32 (int)

   - UInt32 (unsigned int)

   - bool

   - Platform:: String ^

   - Windows:: Foundation:: HResult

   - Platform:: Type ^

   - Veřejná třída Enum (zahrnuje uživatelsky definované výčty)

Další příklad ukazuje, jak definovat vlastní atribut a poté jej inicializovat při jeho použití.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Viz také:

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
