---
title: section
ms.date: 11/04/2016
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 41479d7d8767438d0e59fbe6beb7e435459dcb1b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023240"
---
# <a name="section"></a>section

V souboru .obj, vytvoří oddíl.

## <a name="syntax"></a>Syntaxe

```
#pragma section( "section-name" [, attributes] )
```

## <a name="remarks"></a>Poznámky

Významy pojmů *segmentu* a *části* jsou v tomto tématu zaměnitelné.

Jakmile je definován oddíl, zůstane v platnosti pro zbývající část kompilace. Nicméně je nutné použít [__declspec(allocate)](../cpp/allocate.md) nebo nic budou umístěny do oddílu.

*Název oddílu* je povinný parametr, který bude název oddílu. Název nesmí být v konfliktu s názvy oddíl standard. Zobrazit [/SECTION](../build/reference/section-specify-section-attributes.md) seznam názvů byste neměli používat při tvorbě oddílu.

*atributy* je volitelný parametr, který se skládá z jednoho nebo více oddělených čárkou atributů, které chcete přiřadit k části. Je to možné *atributy* jsou:

|Atribut|Popis|
|-|-|
|**read**|Umožňuje čtení operací s daty.|
|**write**|Umožňuje operací zápisu na data.|
|**Spuštění**|Umožňuje spuštění kódu.|
|**shared**|Sdílené složky v části mezi všechny procesy, které načíst obrázek.|
|**nopage**|Označí oddíl jako nejsou stránkované; užitečné pro ovladače zařízení Win32.|
|**NoCache**|Označí oddílu jako není možné ukládat do mezipaměti; užitečné pro ovladače zařízení Win32.|
|**Zahození**|Označí oddílu jako discardable; užitečné pro ovladače zařízení Win32.|
|**remove**|Označí oddíl jako nejsou rezidentní; virtuální ovladače zařízení (V*x*D) pouze.|

Pokud nezadáte atributy, budou mít číst části a Zapisovat atributy.

## <a name="example"></a>Příklad

V následujícím příkladu první instrukce identifikuje části a jeho atributy. Celé číslo `j` není vložena `mysec` vzhledem k tomu, že nebyla deklarována s `__declspec(allocate)`; `j` přejde do datové části. Celé číslo `i` přejít do `mysec` kvůli jeho `__declspec(allocate)` atribut třídy úložiště.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)