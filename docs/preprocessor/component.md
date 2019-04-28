---
title: komponenta
ms.date: 04/08/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 4870860650a39d27639ad18100ba37ba14aa15c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366911"
---
# <a name="component"></a>komponenta

Kontrolou shromažďování informací o procházení nebo závislostech ze zdrojových souborů.

## <a name="syntax"></a>Syntaxe

> **komponenta #pragma (prohlížeč,** { **na** | **vypnout** } [**,** **odkazy** [**,** *název* ]] **)** \
> **komponenta #pragma (minrebuild na** | **vypnuto)** \
> **komponenta #pragma (mintypeinfo na** | **vypnuto)**

## <a name="remarks"></a>Poznámky

### <a name="browser"></a>Prohlížeč

Toto shromažďování lze zapnout nebo vypnout a lze určit konkrétní názvy, které mají být při shromažďování informací ignorovány.

Použití zapnutí nebo vypnutí řídí shromažďování informací procházení z direktivy pragma forward. Příklad:

```cpp
#pragma component(browser, off)
```

zastaví shromažďování informací o procházení kompilátorem.

> [!NOTE]
> Chcete-li zapnout shromažďování informací o procházení s touto direktivou pragma [informací o procházení nejprve povoleny](../build/reference/building-browse-information-files-overview.md).

`references` Možnost se dá použít s nebo bez něj *název* argument. Pomocí `references` bez *název* Zapne nebo vypne shromažďování odkazů (které se mají shromažďovat, ale bude pokračovat další informace o procházení). Příklad:

```cpp
#pragma component(browser, off, references)
```

zastaví shromažďování informací o odkazech kompilátorem.

Pomocí `references` s *název* a `off` zabrání odkazům na argument *název* povolí, v okně informací o procházení. Tuto syntaxi použijte, pokud chcete ignorovat názvy a typy, které vás nezajímají, a pokud chcete zmenšit velikost souborů s informacemi o procházení. Příklad:

```cpp
#pragma component(browser, off, references, DWORD)
```

odkazy na DWORD od tohoto okamžiku ignoruje. Můžete zapnout shromažďování odkazů na DWORD zpět na pomocí `on`:

```cpp
#pragma component(browser, on, references, DWORD)
```

Toto je jediný způsob, jak obnovit shromažďování odkazů na argument *název*; je nutné explicitně zapnout všechny *název* , který jste vypnuli.

Aby preprocesor zabránil rozšíření argumentu *název* (například rozšíření NULL na hodnotu 0), umístěte kolem něj uvozovky:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Minimální opětovné sestavení

Zastaralá [/Gm (povolení minimálního opětovného sestavení)](../build/reference/gm-enable-minimal-rebuild.md) funkce vyžaduje kompilátor, aby vytvářet a ukládat C++ třídy informací o závislostech, které zabírá místo na disku. Chcete-li ušetřit místo na disku, můžete použít `#pragma component( minrebuild, off )` vždy, když není nutné shromažďovat informace o závislostech, například v neměnných souborech hlaviček. Vložit `#pragma component(minrebuild, on)` po neměnné třídy, chcete-li závislostí kolekce znovu.

### <a name="reduce-type-information"></a>Omezení informací o typech

`mintypeinfo` Možnost snižuje ladicí informace pro zadanou oblast. Objem těchto informací je značný a ovlivňuje soubory .pdb a .obj. V oblasti mintypeinfo nelze ladit třídy a struktury. Použití možnosti mintypeinfo může být užitečné, chcete-li zabránit následujícímu upozornění:

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Další informace najdete v tématu [/Gm (povolení minimálního opětovného sestavení)](../build/reference/gm-enable-minimal-rebuild.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)