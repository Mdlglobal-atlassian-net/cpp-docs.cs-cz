---
title: Atributy (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 815c942194e13fe27e0bb0abe813c61d2ad22fd6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425716"
---
# <a name="attributes-ccx"></a>Atributy (C + +/ CX)

Atribut je zvláštním druhem třídy ref class, která můžou před do hranatých závorek pro typy Windows Runtime a metody k určení určitého chování, k vytvoření metadat. Několik předdefinovaných atributů, například [Windows::Foundation::Metadata::WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)– se běžně používají v jazyce C + +/ CX kódu. Tento příklad ukazuje, jak je atribut aplikován na třídu:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Vlastní atributy

Můžete také definovat vlastní atributy. Vlastní atributy musí splňovat tato pravidla modulu Windows Runtime:

- Vlastní atributy může obsahovat jenom veřejné položky.

- Pole vlastních atributů může být inicializována, když je atribut aplikován na třídu.

- Pole může být jeden z těchto typů:

   - datový typ Int32 (int).

   - UInt32 (unsigned int).

   - bool

   - Platform::String ^

   - Windows::Foundation::HResult

   - Platform::Type^

   - Veřejný výčet tříd (včetně výčtů definovaný uživatelem)

Následující příklad ukazuje, jak definovat vlastní atribut, kterou následně inicializujete při jeho použití.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Viz také

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)