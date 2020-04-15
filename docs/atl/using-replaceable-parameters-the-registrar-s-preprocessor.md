---
title: Použití nahraditelných parametrů (registrátor ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329231"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Použití vyměnitelných parametrů (preprocesor registrátora&#39;)

Nahraditelné parametry umožňují klientovi registrátora určit data za běhu. Za tímto účelem registrátor udržuje náhradní mapu, do které zadá hodnoty spojené s nahraditelnými parametry ve skriptu. Registrátor provádí tyto položky za běhu.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Použití %MODULE%

[Průvodce řízením atl](../atl/reference/atl-control-wizard.md) automaticky generuje `%MODULE%`skript, který používá . Služba ATL používá tento nahraditelný parametr pro skutečné umístění dll nebo exe serveru.

## <a name="concatenating-run-time-data-with-script-data"></a>Zřetězení dat za běhu s daty skriptu

Dalším použitím preprocesoru je zřetězení dat za běhu s daty skriptu. Předpokládejme například, že je potřeba položka, která obsahuje`, 1`úplnou cestu k modulu s řetězcem " " připojeným na konci. Nejprve definujte následující rozšíření:

```
'MySampleKey' = s '%MODULE%, 1'
```

Potom před voláním jedné z metod zpracování skriptů uvedených [v invoking skripty](../atl/invoking-scripts.md), přidejte náhradu do mapy:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Během analýzy skriptu se registrátor `'%MODULE%, 1'` rozbalí `c:\mycode\mydll.dll, 1`na .

> [!NOTE]
> Ve skriptu registrátora je maximální velikost tokenu 4K. (Token je libovolný rozpoznatelný prvek v syntaxi.) To zahrnuje tokeny, které byly vytvořeny nebo rozbaleny preprocesorem.

> [!NOTE]
> Chcete-li nahradit náhradní hodnoty za běhu, odeberte volání ve skriptu do [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) makru. Místo toho jej nahraďte vlastní `UpdateRegistry` metodou, která volá [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)a předejte pole _ATL_REGMAP_ENTRY struktur. Pole _ATL_REGMAP_ENTRY musí mít alespoň jednu položku, která je nastavena na {NULL, NULL}, a tato položka by měla být vždy poslední položkou. V opačném případě bude při volání `UpdateRegistryFromResource` generována chyba narušení přístupu.

> [!NOTE]
> Při vytváření projektu, který vytváří spustitelný soubor, přidá společnost ATL automaticky uvozovky kolem názvu cesty vytvořeného za běhu s parametrem skriptu registrátora **%MODULE%.** Pokud nechcete, aby název cesty obsahoval uvozovky, použijte místo toho nový parametr **%MODULE_RAW%.**
>
> Při vytváření projektu, který vydělá dll, nebude společnost ATL přidávat k názvu cesty uvozovky, pokud je použit **%MODULE%** nebo **%MODULE_RAW%.**

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátora](../atl/creating-registrar-scripts.md)
