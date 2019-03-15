---
title: '&lt;Seznam > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: fd5b97ac518bc4075697da7b6ed88ed46bdd8814
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823370"
---
# <a name="ltlistgt"></a>&lt;list&gt;

\<Listheader – > blokování se používá k definování řádek záhlaví tabulky nebo definice seznamu. Při definování tabulku, stačí zadat položky pro výraz v záhlaví.

## <a name="syntax"></a>Syntaxe

```
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>Parametry

*Termín*<br/>
Termín, který chcete definovat, které budou určené v `description`.

*description*<br/>
Buď položku v odrážkami nebo číslovaný seznam nebo definici `term`.

## <a name="remarks"></a>Poznámky

Každá položka v seznamu není zadán s \<položky > bloku. Při vytváření definice seznamu, budete muset zadat současně `term` a `description`. Ale pro tabulku, seznam s odrážkami nebo číslovaného seznamu, stačí zadat položku pro `description`.

Seznam nebo tabulku můžete mít kolik \<položky > blokuje podle potřeby.

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
