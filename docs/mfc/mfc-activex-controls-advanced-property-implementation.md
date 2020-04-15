---
title: 'MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364654"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností

Tento článek popisuje témata související s implementací rozšířených vlastností v ovládacím prvku ActiveX.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

- [Vlastnosti jen pro čtení a zápis](#_core_read2donly_and_write2donly_properties)

- [Vrácení kódů chyb z vlastnosti](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Vlastnosti jen pro čtení a zápis

Průvodce přidáním vlastností poskytuje rychlou a snadnou metodu implementace vlastností ovládacího prvku jen pro čtení nebo zápis.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Implementace vlastnosti jen pro čtení nebo jen pro zápis

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

   Otevře se [Průvodce přidáním vlastností](../ide/names-add-property-wizard.md).

1. Do pole **Název vlastnosti** zadejte název vaší vlastnosti.

1. V **souboru Typ implementace**klepněte na tlačítko Získat nebo nastavit **metody**.

1. V poli **Typ vlastnosti** vyberte správný typ vlastnosti.

1. Pokud chcete vlastnost jen pro čtení, zrušte zaškrtnutí názvu funkce Set. Pokud chcete vlastnost pouze pro zápis, zrušte název funkce Get.

1. Klikněte na **Finish** (Dokončit).

Když toto provedete, Průvodce přidáním `SetNotSupported` `GetNotSupported` vlastností vloží funkci nebo do položky mapy odeslání namísto normální funkce Set nebo Get.

Pokud chcete změnit existující vlastnost, která má být jen pro čtení nebo jen pro zápis, můžete upravit mapu odeslání ručně a odebrat nepotřebnou funkci Set nebo Get z třídy ovládacího prvku.

Pokud chcete, aby vlastnost byla podmíněně jen pro čtení nebo jen pro zápis (například pouze v případě, že ovládací prvek pracuje `SetNotSupported` `GetNotSupported` v určitém režimu), můžete zadat Set nebo Get funkce, jako normální a volání nebo funkce, kde je to vhodné. Příklad:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Tento ukázkový `SetNotSupported` kód `m_bReadOnlyMode` volá, pokud je datový člen **TRUE**. Pokud **false**, pak vlastnost je nastavena na novou hodnotu.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Vrácení kódů chyb z vlastnosti

Chcete-li označit, že došlo k chybě při pokusu `COleControl::ThrowError` o získání nebo nastavení vlastnosti, použijte funkci, která bere SCODE (stavový kód) jako parametr. Můžete použít předdefinovaný SCODE nebo definovat jeden z vašich vlastních. Seznam předdefinovaných sconetů a pokyny pro definování vlastních scones naleznete [v tématu Zpracování chyb v ovládacím prvku ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v článku Ovládací prvky ActiveX: Rozšířená témata.

Pomocné funkce existují pro nejběžnější předdefinované moduly SCONE, například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)a [COleControl::SetNotPovoleno](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`je určen pouze jako prostředek vrácení chyby z funkce Get nebo Set vlastnosti nebo metody automatizace. Toto jsou pouze časy, které příslušné obslužné rutiny výjimky bude k dispozici v zásobníku.

Další informace o vykazování výjimek v jiných oblastech kódu naleznete v [tématu COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [Zpracování chyb v ovládacím prvku ActiveX v](../mfc/mfc-activex-controls-advanced-topics.md) článku Ovládací prvky ActiveX: Rozšířená témata.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Třída COleControl](../mfc/reference/colecontrol-class.md)
