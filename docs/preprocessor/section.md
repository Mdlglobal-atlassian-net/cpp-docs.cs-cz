---
title: section – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216596"
---
# <a name="section-pragma"></a>section – direktiva pragma

Vytvoří oddíl v souboru. obj.

## <a name="syntax"></a>Syntaxe

> **#pragma oddíl (** "*název oddílu*" [ **,** *atributy* ] **)**

## <a name="remarks"></a>Poznámky

Pojem *segment* a *oddíl* má stejný význam jako v tomto článku.

Po definování oddílu zůstane platnost pro zbytek kompilace platná. Je však nutné použít [__declspec (allocate)](../cpp/allocate.md)nebo nic není umístěno v části.

*název oddílu* je povinný parametr, který se bude jmenovat jako název oddílu. Název nesmí být v konfliktu se standardními názvy oddílů. Seznam názvů, které byste neměli použít při vytváření oddílu, najdete v tématu [/Section](../build/reference/section-specify-section-attributes.md) .

*atributy* je volitelný parametr skládající se z jednoho nebo více atributů oddělených čárkami, které se mají přiřadit k oddílu. Možné *atributy* :

|Atribut|Popis|
|-|-|
|**read**|Povoluje operace čtení dat.|
|**write**|Povoluje operace zápisu na data.|
|**spustit**|Umožňuje spuštění kódu.|
|**sdíleného**|Sdílí část mezi všemi procesy, které načítají bitovou kopii.|
|**na stránce**|Označí oddíl jako nestránkový. Užitečné pro ovladače zařízení Win32.|
|**nocache**|Označí oddíl jako neukládatelné do mezipaměti. Užitečné pro ovladače zařízení Win32.|
|**discard**|Označí oddíl jako zahozený. Užitečné pro ovladače zařízení Win32.|
|**remove**|Označí oddíl jako nerezidentní v paměti. Pouze pro ovladače virtuálních zařízení (V*x*D).|

Pokud nezadáte žádné atributy, oddíl má atributy **pro čtení** a **zápis** .

## <a name="example"></a>Příklad

V tomto příkladu direktiva pragma prvního oddílu identifikuje oddíl a jeho atributy. Celé číslo `j` není vloženo do `mysec` , protože nebylo deklarováno pomocí `__declspec(allocate)`. Místo toho `j` přejde do oddílu data. Celočíselná `i` hodnota se vrátí `mysec` do výsledku jeho `__declspec(allocate)` atributu Class třídy úložiště.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
