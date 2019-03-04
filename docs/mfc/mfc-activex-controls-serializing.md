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
ms.openlocfilehash: 0c1c845640be2dfaa6aeda2defb478afb650b83b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303342"
---
# <a name="mfc-activex-controls-serializing"></a>MFC – ovládací prvky ActiveX: Serializace

Tento článek popisuje, jak k serializaci ovládacího prvku ActiveX. Serializace je proces čtení nebo zápisu do trvalého úložiště média, jako je soubor na disku. Knihovny Microsoft Foundation Class (MFC) poskytuje integrovanou podporu pro serializaci ve třídě `CObject`. `COleControl` rozšiřuje této podpory do ovládacích prvků ActiveX pomocí mechanismem výměny vlastnost.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Serializace pro ovládací prvky ActiveX je implementován tak, že přepíšete [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Tato funkce volá se během načítání a ukládání objekt ovládacího prvku ukládá všechny vlastnosti, které implementuje pomocí členské proměnné nebo členská proměnná se oznámení o změně.

Hlavní problémy související se serializací ovládacího prvku ActiveX naleznete v následujících tématech:

- Implementace `DoPropExchange` funkce k serializaci objektu ovládacího prvku

- [Přizpůsobení procesu serializace](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementace podpora verzí](#_core_implementing_version_support)

##  <a name="_core_implementing_the_dopropexchange_function"></a> Implementace DoPropExchange – funkce

Při použití Průvodce ovládacím prvkem ActiveX se vygenerovat projekt správy několik Výchozí obslužná rutina funkcí jsou automaticky přidány na ovládací prvek třídy, včetně výchozí implementace [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Následující příklad ukazuje kód přidaný do třídy vytvořené pomocí Průvodce ovládacím prvkem ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Pokud chcete k zajištění trvalosti vlastnosti, změnit `DoPropExchange` tak, že přidáte volání funkce vlastnost exchange. Následující příklad ukazuje serializaci vlastní vlastnost logická CircleShape, kde vlastnost CircleShape má výchozí hodnotu **TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

V následující tabulce jsou uvedeny funkce exchange myslitelnými vlastnostmi, které můžete použít k serializaci vlastností ovládacího prvku:

|Funkce výměny vlastnost|Účel|
|---------------------------------|-------------|
|**PX_Blob( )**|Serializuje typ dat vlastnosti binárních rozsáhlých objektů (BLOB).|
|**PX_Bool( )**|Serializuje typu vlastnost typu Boolean.|
|**PX_Color( )**|Serializuje typ vlastnosti.|
|**PX_Currency( )**|Serializuje typu **CY** vlastnosti (měna).|
|**PX_Double( )**|Serializuje typu **double** vlastnost.|
|**PX_Font( )**|Serializuje vlastnost typu písma.|
|**PX_Float( )**|Serializuje typu **float** vlastnost.|
|**Px_iunknown –)**|Serializuje vlastnost typu `LPUNKNOWN`.|
|**Px_long –)**|Serializuje typu **dlouhé** vlastnost.|
|**PX_Picture( )**|Serializuje typ vlastnosti obrázek.|
|**PX_Short( )**|Serializuje typu **krátký** vlastnost.|
|**(PXstring)**|Serializuje typu `CString` vlastnost.|
|**PX_ULong( )**|Serializuje typu **ULONG** vlastnost.|
|**PX_UShort( )**|Serializuje typu **USHORT** vlastnost.|

Další informace o těchto funkcích vlastnost exchange najdete v části [trvalost z ovládacích prvků technologie OLE](../mfc/reference/persistence-of-ole-controls.md) v *odkaz knihovny MFC*.

##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Přizpůsobení výchozí chování DoPropExchange

Výchozí implementace `DoPropertyExchange` (jak je znázorněno v předchozím tématu) provede volání na základní třídu `COleControl`. Toto serializuje sadu vlastností automaticky nepodporuje `COleControl`, které používá více prostoru než serializaci vlastní vlastnosti ovládacího prvku. Odebírá se toto volání umožňuje váš objekt mohl serializovat pouze vlastnosti, které považujete za důležité. Všechny stavy uložených vlastností ovládacího prvku implementoval nebude serializovat, když je uložení nebo načtení objektu ovládacího prvku, pokud explicitně přidat **PX_** volá pro ně.

##  <a name="_core_implementing_version_support"></a> Implementace podpora verzí

Podpora verzí umožňuje upravený ovládací prvek ActiveX pro přidání nových vlastností trvalé a stále moct zjišťovat a načíst trvalý stav vytvořena pomocí dřívější verze ovládacího prvku. Aby ovládací prvek verze k dispozici jako součást jeho trvalá data volání [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) v ovládacím prvku `DoPropExchange` funkce. Toto volání je automaticky vložen, pokud ovládací prvek ActiveX byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX. Je možné odebrat, pokud není nutná podpora verzí. Náklady na velikost ovládacího prvku je však velmi malé (4 bajtů) pro vyšší flexibilitu, která poskytuje podporu verze.

Pokud ovládací prvek nebyl vytvořen pomocí Průvodce ovládacím prvkem ActiveX, přidejte volání do `COleControl::ExchangeVersion` vložíte následující řádek na začátek vašeho `DoPropExchange` – funkce (před voláním `COleControl::DoPropExchange`):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Můžete použít libovolnou **DWORD** jako číslo verze. Generované průvodcem knihovnou ovládací prvek ActiveX projekty používají `_wVerMinor` a `_wVerMajor` jako výchozí. Toto jsou globální konstanty definované v souboru implementace třídy ovládacího prvku ActiveX v projektu. Ve zbývající části vašeho `DoPropExchange` funkce, může volat [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) v každém okamžiku načíst verzi jsou ukládání nebo načítání.

Verze 1 tohoto ovládacího prvku vzorku v následujícím příkladu má pouze vlastnost "ReleaseDate". Verze 2 přidá vlastnost "OriginalDate". Pokud ovládací prvek je nastaven na načíst trvalý stav ze starší verze, inicializuje proměnnou člena pro novou vlastnost na výchozí hodnotu.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Ve výchozím nastavení ovládací prvek "převede" stará data na nejnovější formát. Například pokud verze 2 ovládacího prvku načte data, která byla uložena ve verzi 1, bude zapsána formát verze 2 při uložení znovu. Pokud chcete ovládací prvek k ukládání dat ve formátu posledního přečtení, předejte **FALSE** jako třetí parametr při volání metody `ExchangeVersion`. Tento třetí parametr je nepovinný a je **TRUE** ve výchozím nastavení.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
