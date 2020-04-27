---
title: Použití nahraditelných parametrů (registrátor ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: debbccea5836fa63282b62ff87573160069fb169
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168680"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Použití nahraditelných parametrů (preprocesor&#39;registrátora)

Nahraditelný parametr umožňuje klientovi registrátora zadat data za běhu. V tomto případě registrátor udržuje náhradní mapu, do které vstoupí do hodnot přidružených k nahraditelným parametrům ve vašem skriptu. Registrátor provede tyto položky v době běhu.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Použití% MODULE%

[Průvodce ovládacím prvkem ATL](../atl/reference/atl-control-wizard.md) automaticky vygeneruje skript, který `%MODULE%`používá. ATL používá tento nahraditelný parametr pro skutečné umístění knihoven DLL nebo EXE vašeho serveru.

## <a name="concatenating-run-time-data-with-script-data"></a>Zřetězení běhových dat s daty skriptu

Dalším použitím preprocesoru je zřetězení běhových dat s daty skriptu. Předpokládejme například, že je potřeba zadat položku, která obsahuje úplnou cestu k modulu s řetězcem`, 1`připojeným na konci. Nejdřív definujte následující rozšíření:

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

Před voláním jedné z metod zpracování skriptu, které jsou uvedeny ve [volání skriptů](../atl/invoking-scripts.md), přidejte k mapě náhradu:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Během analýzy skriptu se registrátor rozbalí `'%MODULE%, 1'` do. `c:\mycode\mydll.dll, 1`

> [!NOTE]
> V rámci skriptu registrátora je 4K maximální velikost tokenu. (Token je libovolný rozpoznatelný element v syntaxi.) To zahrnuje tokeny, které byly vytvořeny nebo rozšířeny preprocesorem.

> [!NOTE]
> Chcete-li nahradit nahrazující hodnoty za běhu, odeberte volání ve skriptu do makra [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) . Místo toho ho nahraďte vlastní `UpdateRegistry` metodou, která volá [CAtlModule:: UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule:: UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources), a předejte pole _ATL_REGMAP_ENTRY struktury. Vaše pole _ATL_REGMAP_ENTRY musí mít alespoň jednu položku, která je nastavena na hodnotu {NULL, NULL}, a tato položka by měla být vždy poslední položkou. V opačném případě se při `UpdateRegistryFromResource` volání vygeneruje chyba narušení přístupu.

> [!NOTE]
> Při sestavování projektu, který vytváří výstup spustitelného souboru, knihovna ATL automaticky přidá uvozovky kolem názvu cesty vytvořeného v době běhu s parametrem skriptu **% Module%** registrátora. Pokud nechcete, aby název cesty obsahoval uvozovky, použijte místo toho nový parametr **% MODULE_RAW%** .
>
> Při sestavování projektu, který vytváří výstup knihovny DLL, knihovna ATL do názvu cesty nepřidá uvozovky, pokud je použit **% Module%** nebo **% MODULE_RAW%** .

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátora](../atl/creating-registrar-scripts.md)
