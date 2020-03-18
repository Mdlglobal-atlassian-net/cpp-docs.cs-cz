---
title: '> seznamu &lt;(C++ dokumentační komentáře)'
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: 102cf9f7b1b867a012f662ce786d97012826abd1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439299"
---
# <a name="ltlistgt"></a>&lt;list&gt;

Blok > \<listheader – se používá k definování řádku záhlaví v seznamu tabulek nebo definic. Při definování tabulky stačí zadat položku pro termín v záhlaví.

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

*doby*<br/>
Pojem, který definuje, který bude definován v `description`.

*název*<br/>
Buď položka v seznamu odrážek nebo číslovaný seznam, nebo definice `term`.

## <a name="remarks"></a>Poznámky

Každá položka v seznamu je určena položkou \<> bloku. Při vytváření seznamu definic bude nutné zadat jak `term`, tak `description`. U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description`.

Seznam nebo tabulka může v případě potřeby obsahovat tolik \<položek >.

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

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

## <a name="see-also"></a>Viz také

[Dokumentace XML](xml-documentation-visual-cpp.md)
