---
title: Atributy (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371873"
---
# <a name="attributes-ccx"></a>Atributy (C++/CX)

Atribut je zvláštní druh ref třídy, která může být předřazena v hranatých závorkách na typy a metody prostředí Windows Runtime k určení určitých chování při vytváření metadat. V kódu C++/CX se běžně používá několik předdefinovaných atributů – například [Windows::Foundation::Metadata::WebHostHidden.](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute) Tento příklad ukazuje, jak je atribut použit pro třídu:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Vlastní atributy

Můžete také definovat vlastní atributy. Vlastní atributy musí odpovídat těmto pravidlům prostředí Windows Runtime:

- Vlastní atributy mohou obsahovat pouze veřejná pole.

- Vlastní pole atributů lze inicializovat při použití atributu na třídu.

- Pole může být jedním z těchto typů:

  - int32 (int)

  - uint32 (nepodepsaný int)

  - bool

  - Platforma::Řetězec^

  - Windows::Založení::HVýsledek

  - Platforma::Typ^

  - třída veřejného výčtu (zahrnuje uživatelem definované výčty)

Následující příklad ukazuje, jak definovat vlastní atribut a potom inicializovat při jeho použití.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Viz také

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
