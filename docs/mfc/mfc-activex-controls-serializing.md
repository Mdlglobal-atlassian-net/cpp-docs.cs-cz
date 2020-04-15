---
title: 'MFC – ovládací prvky ActiveX: Serializace'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364562"
---
# <a name="mfc-activex-controls-serializing"></a>MFC – ovládací prvky ActiveX: Serializace

Tento článek popisuje serializaci ovládacího prvku ActiveX. Serializace je proces čtení nebo zápisu na trvalé paměťové médium, například soubor na disku. Knihovna Microsoft Foundation Class (MFC) poskytuje integrovanou `CObject`podporu serializace ve třídě . `COleControl`rozšiřuje tuto podporu na ovládací prvky ActiveX pomocí mechanismu výměny vlastností.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Serializace pro ovládací prvky ActiveX je implementována přepsáním [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Tato funkce, volaná během načítání a ukládání objektu ovládacího prvku, ukládá všechny vlastnosti implementované pomocí členské proměnné nebo členské proměnné s oznámením o změně.

Následující témata pokrývají hlavní problémy související se serializací ovládacího prvku ActiveX:

- Implementace `DoPropExchange` funkce pro serializaci objektu ovládacího prvku

- [Přizpůsobení procesu serializace](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementace podpory verzí](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementace funkce DoPropExchange

Při použití Průvodce ovládacím prvkem ActiveX ke generování řídicího projektu je do třídy ovládacího prvku automaticky přidáno několik výchozích funkcí obslužné rutiny, včetně výchozí implementace [cOleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Následující příklad ukazuje kód přidaný do tříd vytvořených Průvodcem ovládacím prvkem ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Pokud chcete, aby vlastnost trvalá, upravte `DoPropExchange` přidáním volání do funkce výměny vlastností. Následující příklad ukazuje serializaci vlastní logické circleshape vlastnost, kde CircleShape vlastnost má výchozí hodnotu **TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

V následující tabulce jsou uvedeny možné funkce výměny vlastností, které můžete použít k serializaci vlastností ovládacího prvku:

|Funkce výměny majetku|Účel|
|---------------------------------|-------------|
|**PX_Blob( )**|Serializuje vlastnost dat typu Binární velký objekt (BLOB).|
|**PX_Bool( )**|Serializuje vlastnost typu Logická hodnota.|
|**PX_Color( )**|Serializuje vlastnost barvy typu.|
|**PX_Currency( )**|Serializuje vlastnost typu **CY** (měna).|
|**PX_Double( )**|Serializuje vlastnost typu **double.**|
|**PX_Font( )**|Serializuje vlastnost typu Písmo.|
|**PX_Float( )**|Serializuje typ **float** vlastnost.|
|**PX_IUnknown( )**|Serializuje vlastnost typu `LPUNKNOWN`.|
|**PX_Long( )**|Serializuje vlastnost typu **long.**|
|**PX_Picture( )**|Serializuje vlastnost typu Obrázek.|
|**PX_Short( )**|Serializuje vlastnost typu **short.**|
|**PXstring( )**|Serializuje vlastnost typu. `CString`|
|**PX_ULong( )**|Serializuje vlastnost typu **ULONG.**|
|**PX_UShort( )**|Serializuje vlastnost typu **USHORT.**|

Další informace o těchto funkcích výměny vlastností naleznete [v tématu Trvalka ovládacích prvků OLE](../mfc/reference/persistence-of-ole-controls.md) v odkazu *knihovny MFC*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Přizpůsobení výchozího chování doPropExchange

Výchozí implementace `DoPropertyExchange` (jak je znázorněno v předchozím tématu) provede volání základní třídy `COleControl`. Tím serializujem sadu vlastností automaticky `COleControl`podporovaných programem , který využívá více úložného prostoru než serializace pouze vlastních vlastností ovládacího prvku. Odebrání tohoto volání umožňuje objektserializovat pouze ty vlastnosti, které považujete za důležité. Všechny stavy vlastností zásob, které ovládací prvek implementoval, nebudou serializovány při ukládání nebo načítání objektu ovládacího prvku, pokud explicitně nepřidáte **PX_** volání pro ně.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Implementace podpory verzí

Podpora verzí umožňuje revidovanému ovládacímu prvku ActiveX přidat nové trvalé vlastnosti a stále schopen rozpoznat a načíst trvalý stav vytvořený starší verzí ovládacího prvku. Chcete-li zpřístupnit verzi ovládacího prvku jako součást jeho trvalých dat, volejte [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) ve funkci ovládacího `DoPropExchange` prvku. Toto volání je automaticky vloženo, pokud byl ovládací prvek ActiveX vytvořen pomocí Průvodce ovládacím prvkem ActiveX. Může být odebrán, pokud není potřeba podpora verze. Náklady na velikost ovládacího prvku je však velmi malý (4 bajty) pro větší flexibilitu, která poskytuje podporu verze.

Pokud ovládací prvek nebyl vytvořen pomocí Průvodce ovládacím `COleControl::ExchangeVersion` prvkem ActiveX, přidejte volání `DoPropExchange` vložením následujícího `COleControl::DoPropExchange`řádku na začátek funkce (před volání :

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Jako číslo verze můžete použít libovolné **DWORD.** Projekty generované Průvodcem ovládacím `_wVerMinor` `_wVerMajor` prvkem ActiveX a jako výchozí. Jedná se o globální konstanty definované v implementačním souboru třídy ovládacího prvku ActiveX projektu. Ve zbývající části `DoPropExchange` funkce můžete kdykoli volat [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) a načíst verzi, kterou ukládáte nebo načítáte.

V následujícím příkladu má verze 1 tohoto ukázkového ovládacího prvku pouze vlastnost "ReleaseDate". Verze 2 přidá vlastnost "OriginalDate". Pokud je ovládací prvek pokyn k načtení trvalého stavu ze staré verze, inicializuje členproměnné pro novou vlastnost na výchozí hodnotu.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Ve výchozím nastavení ovládací prvek "převede" stará data na nejnovější formát. Například pokud verze 2 ovládacího prvku načte data, která byla uložena ve verzi 1, zapíše formát verze 2 při dalším uložení. Pokud chcete, aby ovládací prvek ukládat data **FALSE** ve formátu poslední `ExchangeVersion`čtení, předat FALSE jako třetí parametr při volání . Tento třetí parametr je volitelný a ve výchozím nastavení je **true.**

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
