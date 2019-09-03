---
title: component – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 578c590bdb4223f173e0249c18d0eea4e78a18db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220477"
---
# <a name="component-pragma"></a>component – direktiva pragma

Řídí shromažďování informací o procházení nebo informací o závislostech v rámci zdrojových souborů.

## <a name="syntax"></a>Syntaxe

> **součást #pragma (Browser;** { **on** | **off** } [ **;** **References** [ **;** *Name* ]] **)**  \
> **součást #pragma (minrebuild,** { **on** | **off** } **)**  \
> **součást #pragma (mintypeinfo,** { **on** | **off** } **)**

## <a name="remarks"></a>Poznámky

### <a name="browser"></a>Browser

Toto shromažďování lze zapnout nebo vypnout a lze určit konkrétní názvy, které mají být při shromažďování informací ignorovány.

Použití zapnutí nebo vypnutí řídí shromažďování informací procházení z direktivy pragma forward. Příklad:

```cpp
#pragma component(browser, off)
```

zastaví shromažďování informací o procházení kompilátorem.

> [!NOTE]
> Chcete-li zapnout shromažďování informací o procházení pomocí této direktivy pragma, [je nutné nejprve povolit informace o procházení](../build/reference/building-browse-information-files-overview.md).

Možnost **odkazy** lze použít s argumentem *Name* nebo bez něj. Použití **odkazů** bez *názvu* zapíná nebo vypíná shromažďování odkazů (ale další informace o procházení jsou stále shromažďovány). Příklad:

```cpp
#pragma component(browser, off, references)
```

zastaví shromažďování informací o odkazech kompilátorem.

Použití **odkazů** s *názvem* a **vypnuto** zabraňuje zobrazování odkazů na *název* v okně informace o procházení. Tuto syntaxi použijte, pokud chcete ignorovat názvy a typy, které vás nezajímají, a pokud chcete zmenšit velikost souborů s informacemi o procházení. Příklad:

```cpp
#pragma component(browser, off, references, DWORD)
```

ignoruje odkazy na DWORD z tohoto okamžiku předá. Shromažďování odkazů na DWORD můžete znovu zapnout pomocí:

```cpp
#pragma component(browser, on, references, DWORD)
```

Toto je jediný způsob, jak obnovit shromažďování odkazů na *název*; musíte explicitně zapnout všechny *názvy* , které jste vypnuli.

Chcete-li zabránit preprocesoru v rozšíření *názvu* (například zvětšení hodnoty null na hodnotu 0), vložte kolem něj uvozovky:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Minimální opětovné sestavení

Zastaralá funkce [/GM (povolit minimální opětovné sestavení)](../build/reference/gm-enable-minimal-rebuild.md) vyžaduje, aby kompilátor vytvořil a uložil C++ informace o závislostech třídy, které přebírají místo na disku. Chcete-li ušetřit místo na disku, `#pragma component( minrebuild, off )` můžete použít vždy, když nepotřebujete shromažďovat informace o závislostech, například v nezměněných hlavičkových souborech. Vložení `#pragma component( minrebuild, on )` po nezměněných tříd pro opětovné zapnutí kolekce závislostí.

### <a name="reduce-type-information"></a>Snížení informací o typu

`mintypeinfo` Možnost zmenší informace o ladění pro určenou oblast. Objem těchto informací je značný a ovlivňuje soubory .pdb a .obj. V oblasti mintypeinfo nelze ladit třídy a struktury. Použití možnosti mintypeinfo může být užitečné, chcete-li zabránit následujícímu upozornění:

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Další informace naleznete v tématu možnost kompilátoru [/GM (povolit minimální opětovné sestavení)](../build/reference/gm-enable-minimal-rebuild.md) .

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
